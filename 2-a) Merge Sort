#include <stdio.h>
#include <math.h>
#include <time.h>

void Merge(int a[], int low, int mid, int high) {
    int i, j, k, temp[high - low + 1];
    i = low; // index of first element in the first half
    k = 0; // index of temporary array temp
    j = mid + 1; // index of first element in the second half

    // Merge the two parts into temp[].
    while (i <= mid && j <= high) {
        if (a[i] < a[j]) {
            temp[k] = a[i];
            k++;
            i++;
        } else {
            temp[k] = a[j];
            k++;
            j++;
        }
    }

    // Insert all the remaining values from i to mid into temp[].
    while (i <= mid) {
        temp[k] = a[i];
        k++;
        i++;
    }

    // Insert all the remaining values from j to high into temp[].
    while (j <= high) {
        temp[k] = a[j];
        k++;
        j++;
    }

    // Assign sorted data stored in temp[] to a[].
    for (i = low; i <= high; i++) {
        a[i] = temp[i - low];
    }
}

// A function to split array into two parts.
void MergeSort(int a[], int low, int high) {
    int mid;
    if (low < high) { // array is having more than one element
        mid = (low + high) / 2;
        // Split the data into two halves.
        MergeSort(a, low, mid); // applying mergesort on the first half
        MergeSort(a, mid + 1, high);
        // Merge them to get sorted output.
        Merge(a, low, mid, high);
    }
}

int main() {
    int n, a[100], k;
    clock_t st, et;
    double ts;

    printf("Enter how many numbers: ");
    scanf("%d", &n);

    printf("\nThe random numbers are:\n");
    for (k = 1; k <= n; k++) {
        // Generates a random number between 50 and 100.
        a[k] = rand() % (100 - 50 + 1) + 50;
        printf("%d\t", a[k]);
    }

    st = clock();

    for (k = 1; k < 10000; k++) {
        MergeSort(a, 1, n);
    }

    et = clock(); // Approximate processor time that is consumed
    ts = (double)(et - st) / CLOCKS_PER_SEC;
    ts = ts / 10000;

    printf("\nSorted numbers are:\n");
    for (k = 1; k <= n; k++) {
        printf("%d\t", a[k]);
    }

    printf("\nThe time taken is %e sec", ts);

    return 0;
}
