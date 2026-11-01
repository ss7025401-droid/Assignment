#include <stdio.h>

// Function to insert an element into a sorted array.
// Returns the updated number of elements in the array.
int insertIntoSorted(int arr[], int n, int capacity, int key) {
    // 1. Check if the array has reached its maximum capacity
    if (n >= capacity) {
        printf("\nError: Array is full. Cannot insert %d.\n", key);
        return n;
    }

    int i = n - 1;

    // 2. Start from the right and shift elements greater than 'key' one position to the right
    while (i >= 0 && arr[i] > key) {
        arr[i + 1] = arr[i];
        i--;
    }

    // 3. Insert the key into the vacant position
    arr[i + 1] = key;

    // 4. Return the new size of the array
    return n + 1;
}

int main() {
    int capacity = 10; 
    int arr[10] = {12, 16, 20, 40, 50, 70}; // Pre-allocated array with extra space
    int n = 6;                              // Current number of active elements
    int key = 25;                           // Element to insert

    printf("Before insertion: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    // Perform insertion
    n = insertIntoSorted(arr, n, capacity, key);

    printf("\nAfter insertion:  ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
