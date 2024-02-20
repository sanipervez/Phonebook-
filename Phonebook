import java.io.*;

//initial ways to read in/retrieve values for name
class Name {
	public Name(String last, String first) {
		this.last = last;
		this.first = first;
	}

	public Name(String first) {
		this("", first);
	}

	public String getFirstLast() {
		return first + " " + last;
	}

	public String getOfficial() {
		return last + ", " + first;
	}

	public String getInitials() {
		return first.charAt(0) + "." + last.charAt(0) + ".";
	}

	public boolean equals(Name other) {
		return first.equals(other.first) && last.equals(other.last);
	}

	public String toString() {
		return first + " " + last;
	}

	public static Name read(Scanner scanner) {
		if (!scanner.hasNext()) {
			return null;
		}
		String last = scanner.next();
		String first = scanner.next();
		return new Name(last, first);
	}

	public static Name read2(Scanner scanner) {
		if (!scanner.hasNext()) {
			String last = "";
			String first = "";
			return new Name(last, first);
		}
		String last = scanner.next();
		String first = scanner.next();
		return new Name(last, first);
	}

	private String first, last;
}

class PhoneNumber {
	public PhoneNumber() {
		this("");
	}

	public PhoneNumber(String number) {
		this.number = number;
	}

	public String getAreaCode() {
		return number.substring(1, 4);
	}

	public String getExchange() {
		return number.substring(5, 8);
	}

	public String getLineNumber() {
		return number.substring(9, 13);
	}

	public boolean isTollFree() {
		if (number.substring(1, 2).equals("8")) {
			return true;
		} else {
			return false;
		}
	}

	public boolean equals(PhoneNumber other) {
		return number.equals(other.number);
	}

	public String toString() {
		return number;
	}
	//read in new number
	public static PhoneNumber read(Scanner scanner) {
		if (!scanner.hasNext()) {
			return null;
		}
		String number = scanner.next();
		return new PhoneNumber(number);
	}

	public static PhoneNumber read2(Scanner scanner2) {
		if (!scanner2.hasNext()) {
			String number = "";
			return new PhoneNumber(number);
		}
		String number = scanner2.next();
		return new PhoneNumber(number);
	}

	private String number;
}

class PhonebookEntry {
	private Name name;
	PhoneNumber phoneNumber;

	public PhonebookEntry() {
	}

	public PhonebookEntry(Name name, PhoneNumber phoneNumber) {
		this.name = name;
		this.phoneNumber = phoneNumber;
	}

	public Name getName() {
		return this.name;
	}

	public PhoneNumber getPhoneNumber() {
		return this.phoneNumber;
	}

	public void call() {
		if (phoneNumber.isTollFree()) {
			System.out.println("Dialing (toll-free) " + getName() + ": " + getPhoneNumber());
		} else {
			System.out.println("Dialing " + getName() + ": " + getPhoneNumber());
		}
	}

	public String toString() {
		return name + ":";
	}

	public boolean equals(PhonebookEntry other) {
		return name.equals(other.name) && phoneNumber.equals(other.phoneNumber);
	}

	public static PhonebookEntry read(Scanner scanner) {
		if (!scanner.hasNext()) {
			return null;
		}
		String first = scanner.next();
		String last = scanner.next();
		Name name = new Name(first, last);
		PhoneNumber number = new PhoneNumber(scanner.next());
		return new PhonebookEntry(name, number);
	}

	public static PhonebookEntry read2(Scanner scanner) {
		if (!scanner.hasNext()) {
			Name name = new Name("", "");
			PhoneNumber number = new PhoneNumber("");
			return new PhonebookEntry(name, number);
		}
		String first = scanner.next();
		String last = scanner.next();
		Name name = new Name(first, last);
		PhoneNumber number = new PhoneNumber(scanner.next());
		return new PhonebookEntry(name, number);
	}
}

class Phonebook {
	private PhonebookEntry[] arr;
	final int size = 100;
	public Phonebook() {
		
	}
	
	public Phonebook(Scanner input, int size) {
		arr = new PhonebookEntry[size];
		PhonebookEntry pbe = PhonebookEntry.read(input);
		int index = 0;
		while (pbe != null) {
			try {
			if (index >= arr.length) {
				throw new Exception();
			}
			}
			catch (Exception ex) {
				System.out.println("Exception! The phonebook capacity has exceeded it's limit - increase size of the array");
			}
			arr[index] = pbe;
			index++;
			pbe = PhonebookEntry.read(input);
		}
	}

	public String returnlookup(Scanner keyboard) {
		System.out.print("last name? ");
		String last = keyboard.next();
		System.out.print("first name? ");
		String first = keyboard.next();
		Name name = new Name(last, first);
		int index = 0;
		while (index < arr.length && arr[index] != null) {
			if (arr[index].getName().equals(name)) {
				System.out.print(first + " " + last + "'s phone number is ");
				return arr[index].getPhoneNumber().toString();
			}
			index++;
		}
		return "-- Name not found";
	}

	public String returnreverse(Scanner keyboard) {
		System.out.print("phone number (xxx-xxx-xxxx)? ");
		String number = keyboard.next();
		String result = "";
		int index = 0;
		PhoneNumber num = new PhoneNumber(number);
		while (index < arr.length && arr[index] != null) {
			if (arr[index].getPhoneNumber().equals(num)) {
				result = number + " belongs to " + arr[index].getName();
				return result;
			}
			index++;
		}
		result = "-- Phone number not found";
		return result;
	}
}
class PhonebookApp {
	public static void main(String[] args) throws IOException {
		final int size = 100;
		try {
			Scanner input = new Scanner(new File("phonebook.text"));
			Scanner keyboard = new Scanner(System.in);
			Phonebook pb = new Phonebook(input, size);
			int index = 0;
			int lookupcounter = 0;
			int reversecounter = 0;
			char var;
			boolean testCases = true;
			while (testCases) {
				System.out.print("lookup, reverse-lookup, quit (l/r/q)? ");
				switch (var = keyboard.next().charAt(0)) {
				case 'r':
					System.out.println(pb.returnreverse(keyboard)) + "\n";
					reversecounter++;
					break;
				case 'l':
					System.out.println(pb.returnlookup(keyboard) + "\n");
					lookupcounter++;
					break;
				case 'q':
					System.out.println();
					System.out.println(lookupcounter + " lookups performed");
					System.out.print(reversecounter + " reverse lookups performed" "\n");
					boolbool = false;
					break;
				default:
					System.out.println("this is not a lookup, reverse-lookup or q");
					break;

				}

			}
		} catch (FileNotFoundException a) {
			a.printStackTrace();
		} catch (Exception a) {
			a.printStackTrace();
		}
	}
}
