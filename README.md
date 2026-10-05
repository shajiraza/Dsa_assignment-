Q1. Design and implement a Stack using an array without using any built-in stack library.

Perform the following operations:

* PUSH(x)
* POP()
* PEEK()
* DISPLAY()

The program must handle Stack Overflow and Stack Underflow conditions.

Also explain the time complexity and space complexity of each operation and what happens when the fixed stack capacity is exceeded. 

#include <iostream>
using namespace std;

#define MAX 5

int stack[MAX];
int top = -1;

// PUSH
void push(int x)
{
    if (top == MAX - 1)
    {
        cout << "Stack Overflow!" << endl;
    }
    else
    {
        top++;
        stack[top] = x;
        cout << x << " pushed into stack." << endl;
    }
}

// POP
void pop()
{
    if (top == -1)
    {
        cout << "Stack Underflow!" << endl;
    }
    else
    {
        cout << stack[top] << " popped from stack." << endl;
        top--;
    }
}

// PEEK
void peek()
{
    if (top == -1)
    {
        cout << "Stack is empty!" << endl;
    }
    else
    {
        cout << "Top element is: " << stack[top] << endl;
    }
}

// DISPLAY
void display()
{
    if (top == -1)
    {
        cout << "Stack is empty!" << endl;
    }
    else
    {
        cout << "Stack elements are:" << endl;

        for (int i = top; i >= 0; i--)
        {
            cout << stack[i] << endl;
        }
    }
}

int main()
{
    int choice, value;

    while (true)
    {
        cout << "\n----- STACK MENU -----" << endl;
        cout << "1. PUSH" << endl;
        cout << "2. POP" << endl;
        cout << "3. PEEK" << endl;
        cout << "4. DISPLAY" << endl;
        cout << "5. EXIT" << endl;

        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1:
                cout << "Enter value: ";
                cin >> value;
                push(value);
                break;

            case 2:
                pop();
                break;

            case 3:
                peek();
                break;

            case 4:
                display();
                break;

            case 5:
                return 0;

            default:
                cout << "Invalid choice!" << endl;
        }
    }

    return 0;
}







Q2. Implement a Circular Queue using an array.

The queue should support:

* ENQUEUE(x)
* DEQUEUE()
* FRONT()
* DISPLAY()

The implementation must correctly distinguish between a full queue and an empty queue.

Also compare Circular Queue with Linear Queue. 



#include <iostream>
using namespace std;

#define MAX 5

int queue[MAX];

int front = -1;
int rear = -1;

// ENQUEUE
void enqueue(int x)
{
    if ((rear + 1) % MAX == front)
    {
        cout << "Queue Overflow! Queue is full." << endl;
    }
    else
    {
        if (front == -1)
        {
            front = 0;
            rear = 0;
        }
        else
        {
            rear = (rear + 1) % MAX;
        }

        queue[rear] = x;

        cout << x << " inserted into queue." << endl;
    }
}

// DEQUEUE
void dequeue()
{
    if (front == -1)
    {
        cout << "Queue Underflow! Queue is empty." << endl;
    }
    else
    {
        cout << queue[front] << " deleted from queue." << endl;

        if (front == rear)
        {
            front = -1;
            rear = -1;
        }
        else
        {
            front = (front + 1) % MAX;
        }
    }
}

// FRONT
void getFront()
{
    if (front == -1)
    {
        cout << "Queue is empty!" << endl;
    }
    else
    {
        cout << "Front element is: " << queue[front] << endl;
    }
}

// DISPLAY
void display()
{
    if (front == -1)
    {
        cout << "Queue is empty!" << endl;
    }
    else
    {
        cout << "Queue elements are: ";

        int i = front;

        while (true)
        {
            cout << queue[i] << " ";

            if (i == rear)
                break;

            i = (i + 1) % MAX;
        }

        cout << endl;
    }
}

int main()
{
    int choice, value;

    while (true)
    {
        cout << "\n----- CIRCULAR QUEUE MENU -----" << endl;
        cout << "1. ENQUEUE" << endl;
        cout << "2. DEQUEUE" << endl;
        cout << "3. FRONT" << endl;
        cout << "4. DISPLAY" << endl;
        cout << "5. EXIT" << endl;

        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1:
                cout << "Enter value: ";
                cin >> value;
                enqueue(value);
                break;

            case 2:
                dequeue();
                break;

            case 3:
                getFront();
                break;

            case 4:
                display();
                break;

            case 5:
                return 0;

            default:
                cout << "Invalid choice!" << endl;
        }
    }

    return 0;
}
