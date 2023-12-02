# Assignment-3.2-Implementing-the-Java-Collections-Framework
/*
 Sanyerlis Camacaro - Sanyerliscamacaro@uat.edu - CSC263
 Assignment 3.2: Implementing the Java Collections Framework

Overview:
This assignment will help you to put your hand on the Java Collections Framework implementation.

Guidelines:
Using the book (Chapter 16) and online resources: Write me a Java implementation for all of:
Linked Lists, Array Lists, Stack, Queue, and Hash Tables. Don’t forget to write the necessary
test classes for each one of them.

About Code:
This code is a Java program that implements various data structures (Linked List, Array List,
Stack, Queue, and Hash Table) and allows the user to interactively test and demonstrate each of these data structures.
The program provides a menu for the user to choose which data structure to test and performs
the corresponding operations based on the user's input.
 */
// Importing the Scanner class from the java.util package.
import java.util.*;

// Node class for Linked List
class Node<T> {
    T data;
    Node<T> next;

    // Constructor to initialize a node with data
    public Node(T data) {
        this.data = data;
        this.next = null;
    }
}

// Linked List implementation
class MyLinkedList<T> {
    Node<T> head;

    // Method to add a new element to the linked list
    public void add(T data) {
        Node<T> newNode = new Node<>(data);
        if (head == null) {
            head = newNode;
        } else {
            Node<T> current = head;
            // Traverse to the end of the list
            while (current.next != null) {
                current = current.next;
            }
            // Add the new node at the end
            current.next = newNode;
        }
    }

    // Method to display the elements of the linked list
    public void display() {
        Node<T> current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}

// Array List implementation
class MyArrayList<T> {
    ArrayList<T> list;

    // Constructor to initialize an array list
    public MyArrayList() {
        this.list = new ArrayList<>();
    }

    // Method to add a new element to the array list
    public void add(T data) {
        list.add(data);
    }

    // Method to display the elements of the array list
    public void display() {
        for (T element : list) {
            System.out.print(element + " ");
        }
        System.out.println();
    }
}

// Stack implementation
class MyStack<T> {
    LinkedList<T> stack;

    // Constructor to initialize a stack
    public MyStack() {
        this.stack = new LinkedList<>();
    }

    // Method to push a new element onto the stack
    public void push(T data) {
        stack.push(data);
    }

    // Method to pop an element from the stack
    public T pop() {
        return stack.pop();
    }

    // Method to display the elements of the stack
    public void display() {
        Iterator<T> iterator = stack.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
        System.out.println();
    }
}

// Queue implementation
class MyQueue<T> {
    LinkedList<T> queue;

    // Constructor to initialize a queue
    public MyQueue() {
        this.queue = new LinkedList<>();
    }

    // Method to enqueue a new element into the queue
    public void enqueue(T data) {
        queue.offer(data);
    }

    // Method to dequeue an element from the queue
    public T dequeue() {
        return queue.poll();
    }

    // Method to display the elements of the queue
    public void display() {
        Iterator<T> iterator = queue.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
        System.out.println();
    }
}

// Hash Table implementation
class MyHashTable<K, V> {
    HashMap<K, V> hashTable;

    // Constructor to initialize a hash table
    public MyHashTable() {
        this.hashTable = new HashMap<>();
    }

    // Method to put a key-value pair into the hash table
    public void put(K key, V value) {
        hashTable.put(key, value);
    }

    // Method to get the value associated with a key from the hash table
    public V get(K key) {
        return hashTable.get(key);
    }

    // Method to display all key-value pairs in the hash table
    public void display() {
        for (Map.Entry<K, V> entry : hashTable.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        Scanner nameScanner = new Scanner(System.in);
        System.out.print("\nHello, Welcome to Java Collections Framework Demo!");
        System.out.print("\nPlease enter your name: ");
        String userName = nameScanner.nextLine();
        System.out.println("Welcome, " + userName + "!");

        Scanner choiceScanner = new Scanner(System.in);

        boolean exitProgram = false;

        while (!exitProgram) {
            System.out.println("Choose a data structure to test:");
            // Display menu options for different data structures
            System.out.println("1. Linked List - A linear data structure where elements are stored in a sequence.");
            System.out.println("2. Array List - Similar to a dynamic array, allows fast access and dynamic resizing.");
            System.out.println("3. Stack - Follows Last In First Out order, like a stack of plates.");
            System.out.println("4. Queue - Follows First In First Out order, like a queue in a line.");
            System.out.println("5. Hash Table - Uses key-value pairs for fast data retrieval.");
            System.out.println("6. Test another data structure");
            System.out.println("7. Exit");

            System.out.print("Enter the number of your choice: ");
            // Get user choice from the menu
            int choice = choiceScanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Example of Linked List:");
                    System.out.println("Adding elements: 1 -> 2 -> 3 -> 4");
                    // Test the Linked List implementation
                    testMyLinkedList();
                    break;
                case 2:
                    System.out.println("Example of Array List:");
                    System.out.println("Adding elements: 10, 20, 30, 40");
                    // Test the Array List implementation
                    testMyArrayList();
                    break;
                case 3:
                    System.out.println("Example of Stack:");
                    System.out.println("Pushing elements onto the stack: A, B, C");
                    // Test the Stack implementation
                    testMyStack();
                    break;
                case 4:
                    System.out.println("Example of Queue:");
                    System.out.println("Enqueuing elements into the queue: X, Y, Z");
                    // Test the Queue implementation
                    testMyQueue();
                    break;
                case 5:
                    System.out.println("Example of Hash Table:");
                    System.out.println("Putting key-value pairs into the hash table: {Name=John, Age=25}");
                    // Test the Hash Table implementation
                    testMyHashTable();
                    break;
                case 6:
                    // Continue to the next iteration of the loop to allow testing another data structure
                    break;
                case 7:
                    // Set exitProgram to true to exit the loop and end the program
                    exitProgram = true;
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 7.");
            }
        }

        // Close scanners to prevent resource leaks
        nameScanner.close();
        choiceScanner.close();
        System.out.println("Goodbye, " + userName + "! Thank you for testing different Data Structures. You are exiting the program.");
    }

    // Method to test the Linked List implementation
    public static void testMyLinkedList() {
        MyLinkedList<String> linkedList = new MyLinkedList<>();
        Scanner inputScanner = new Scanner(System.in);
        System.out.println("Enter items for the Linked List (enter 'done' to finish):");
        String input;
        while (true) {
            System.out.print("Item: ");
            input = inputScanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            // Add input to the Linked List
            linkedList.add(input);
        }
        System.out.print("Linked List: ");
        // Display the contents of the Linked List
        linkedList.display();
    }

    // Method to test the Array List implementation
    public static void testMyArrayList() {
        MyArrayList<String> arrayList = new MyArrayList<>();
        Scanner inputScanner = new Scanner(System.in);
        System.out.println("Enter items for the Array List (enter 'done' to finish):");
        String input;
        while (true) {
            System.out.print("Item: ");
            input = inputScanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            // Add input to the Array List
            arrayList.add(input);
        }
        System.out.print("Array List: ");
        // Display the contents of the Array List
        arrayList.display();
    }

    // Method to test the Stack implementation
    public static void testMyStack() {
        MyStack<String> stack = new MyStack<>();
        Scanner inputScanner = new Scanner(System.in);
        System.out.println("Enter items for the Stack (enter 'done' to finish):");
        String input;
        while (true) {
            System.out.print("Item: ");
            input = inputScanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            // Push input onto the Stack
            stack.push(input);
        }
        System.out.print("Stack: ");
        // Display the contents of the Stack
        stack.display();
        if (!stack.stack.isEmpty()) {
            System.out.println("Popped item: " + stack.pop());
        }
    }

    // Method to test the Queue implementation
    public static void testMyQueue() {
        MyQueue<String> queue = new MyQueue<>();
        Scanner inputScanner = new Scanner(System.in);
        System.out.println("Enter items for the Queue (enter 'done' to finish):");
        String input;
        while (true) {
            System.out.print("Item: ");
            input = inputScanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            // Enqueue input into the Queue
            queue.enqueue(input);
        }
        System.out.print("Queue: ");
        // Display the contents of the Queue
        queue.display();
        if (!queue.queue.isEmpty()) {
            System.out.println("Dequeued item: " + queue.dequeue());
        }
    }

    // Method to test the Hash Table implementation
    public static void testMyHashTable() {
        MyHashTable<String, String> hashTable = new MyHashTable<>();
        Scanner inputScanner = new Scanner(System.in);
        System.out.println("Enter key-value pairs for the Hash Table (enter 'done' to finish):");
        String key, value;
        while (true) {
            System.out.print("Key: ");
            key = inputScanner.nextLine();
            if (key.equalsIgnoreCase("done")) {
                break;
            }
            System.out.print("Value: ");
            value = inputScanner.nextLine();
            // Put key-value pair into the Hash Table
            hashTable.put(key, value);
        }
        System.out.println("Hash Table:");
        // Display all key-value pairs in the Hash Table
        hashTable.display();
        System.out.print("Enter a key to retrieve its value: ");
        String keyToRetrieve = inputScanner.nextLine();
        System.out.println("Value for '" + keyToRetrieve + "': " + hashTable.get(keyToRetrieve));
    }
}
