package coverage

import (
	"fmt"
	"os"
	"reflect"
	"sort"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

const matrixFirst = "1 2\n3 4"
const matrixSecond = "1 2 3\n4 5 6\n7 8 9\n10 11 12"

func TestLen(t *testing.T) {
	tData := []struct {
		A        People
		Expected int
	}{
		{A: People{
			Person{firstName: "A", lastName: "B", birthDay: time.Now()},
			Person{firstName: "A", lastName: "B", birthDay: time.Now()},
			Person{firstName: "A", lastName: "B", birthDay: time.Now()},
			Person{firstName: "A", lastName: "B", birthDay: time.Now()},
		}, Expected: 4},

		{A: People{}, Expected: 0},

		{A: People{
			Person{firstName: "A", lastName: "B", birthDay: time.Now()},
		}, Expected: 1},
	}

	for k, v := range tData {
		got := v.A.Len()

		if got != v.Expected {
			t.Errorf("[%d] expected: %d, got %d", k, v.Expected, got)
		}
	}
}

func TestLess(t *testing.T) {
	now := time.Now()

	tData := []struct {
		A        People
		i        int
		j        int
		Expected bool
	}{
		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 0, j: 1, Expected: true},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 1, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 0, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 0, j: 1, Expected: true},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 1, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "B", lastName: "B", birthDay: now},
		}, i: 0, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "B", birthDay: now},
		}, i: 0, j: 1, Expected: true},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "B", birthDay: now},
		}, i: 1, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "B", birthDay: now},
		}, i: 0, j: 0, Expected: false},

		{A: People{
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "B", birthDay: now},
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "B", birthDay: now},
		}, i: 4, j: 5, Expected: true},
	}

	for k, v := range tData {
		got := v.A.Less(v.i, v.j)

		if got != v.Expected {
			t.Errorf("[%d] expected: %t, got %t", k, v.Expected, got)
		}
	}
}

func TestSwap(t *testing.T) {
	now := time.Now()

	tData := []struct {
		A        People
		i        int
		j        int
		Expected People
	}{{A: People{
		Person{firstName: "A", lastName: "B", birthDay: now},
		Person{firstName: "D", lastName: "B", birthDay: now},
		Person{firstName: "C", lastName: "B", birthDay: now},
		Person{firstName: "B", lastName: "B", birthDay: now},
	},
		i: 1, j: 3,
		Expected: People{
			Person{firstName: "A", lastName: "B", birthDay: now},
			Person{firstName: "B", lastName: "B", birthDay: now},
			Person{firstName: "C", lastName: "B", birthDay: now},
			Person{firstName: "D", lastName: "B", birthDay: now},
		}},
	}

	for k, v := range tData {
		v.A.Swap(v.i, v.j)

		if !reflect.DeepEqual(v.A, v.Expected) {
			t.Error(k, v.Expected)
		}
	}
}

func TestSort(t *testing.T) {
	now := time.Now()

	tData := []struct {
		A        People
		Expected People
	}{
		{A: People{
			Person{firstName: "A", lastName: "B", birthDay: now},
			Person{firstName: "D", lastName: "B", birthDay: now},
			Person{firstName: "C", lastName: "B", birthDay: now},
			Person{firstName: "B", lastName: "B", birthDay: now},
			Person{firstName: "A", lastName: "A", birthDay: now},
			Person{firstName: "D", lastName: "A", birthDay: now},
			Person{firstName: "C", lastName: "A", birthDay: now},
			Person{firstName: "B", lastName: "A", birthDay: now},
			Person{firstName: "A", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "D", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "C", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
			Person{firstName: "B", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
		},
			Expected: People{
				Person{firstName: "A", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
				Person{firstName: "B", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
				Person{firstName: "C", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
				Person{firstName: "D", lastName: "A", birthDay: now.Add(time.Hour * time.Duration(5))},
				Person{firstName: "A", lastName: "A", birthDay: now},
				Person{firstName: "A", lastName: "B", birthDay: now},
				Person{firstName: "B", lastName: "A", birthDay: now},
				Person{firstName: "B", lastName: "B", birthDay: now},
				Person{firstName: "C", lastName: "A", birthDay: now},
				Person{firstName: "C", lastName: "B", birthDay: now},
				Person{firstName: "D", lastName: "A", birthDay: now},
				Person{firstName: "D", lastName: "B", birthDay: now},
			}},
	}

	for k, v := range tData {
		sort.Sort(v.A)

		if !reflect.DeepEqual(v.A, v.Expected) {
			t.Error(k, v.A)
		}
	}
}

func TestMatrixNew(t *testing.T) {
	tData := []struct {
		input    string
		Expected *Matrix
		Err      error
	}{
		{
			input:    "1 1\n 1 1",
			Expected: &Matrix{rows: 2, cols: 2, data: []int{1, 1, 1, 1}},
			Err:      nil,
		},
		{
			input:    "10 10\n10 10\n10 10",
			Expected: &Matrix{rows: 3, cols: 2, data: []int{10, 10, 10, 10, 10, 10}},
			Err:      nil,
		},
		{
			input:    "1 1\n1 1 1",
			Expected: nil,
			Err:      fmt.Errorf("Rows need to be the same length"),
		},
	}

	for k, v := range tData {
		got, err := New(v.input)

		if err != nil && err.Error() != v.Err.Error() {
			t.Errorf("[%d] error happend while not expected: %s", k, err.Error())
		}

		if !reflect.DeepEqual(got, v.Expected) {
			t.Error(k, v.Expected, got)
		}
	}
}

func TestMatrixRows(t *testing.T) {
	first, _ := New(matrixFirst)
	second, _ := New(matrixSecond)

	tData := []struct {
		input    Matrix
		Expected [][]int
	}{
		{
			input:    *first,
			Expected: [][]int{{1, 2}, {3, 4}},
		},
		{
			input:    *second,
			Expected: [][]int{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}, {10, 11, 12}},
		},
	}

	for k, v := range tData {
		got := v.input.Rows()

		if !reflect.DeepEqual(got, v.Expected) {
			t.Error(k, v.Expected, got)
		}
	}
}

func TestMatrixCols(t *testing.T) {
	first, _ := New(matrixFirst)
	second, _ := New(matrixSecond)

	tData := []struct {
		input    Matrix
		Expected [][]int
	}{
		{
			input:    *first,
			Expected: [][]int{{1, 3}, {2, 4}},
		},
		{
			input:    *second,
			Expected: [][]int{{1, 4, 7, 10}, {2, 5, 8, 11}, {3, 6, 9, 12}},
		},
	}

	for k, v := range tData {
		got := v.input.Cols()

		if !reflect.DeepEqual(got, v.Expected) {
			t.Error(k, v.Expected, got)
		}
	}
}

func TestMatrixSet(t *testing.T) {
	first, _ := New(matrixFirst)
	second, _ := New(matrixSecond)

	tData := []struct {
		matrix         *Matrix
		row            int
		col            int
		value          int
		Expected       *Matrix
		ExpectedOutput bool
	}{
		{
			matrix:         first,
			row:            1,
			col:            0,
			value:          5,
			Expected:       &Matrix{rows: 2, cols: 2, data: []int{1, 2, 5, 4}},
			ExpectedOutput: true,
		},
		{
			matrix:         second,
			row:            2,
			col:            0,
			value:          15,
			Expected:       &Matrix{rows: 4, cols: 3, data: []int{1, 2, 3, 4, 5, 6, 15, 8, 9, 10, 11, 12}},
			ExpectedOutput: true,
		},
	}

	for k, v := range tData {
		output := v.matrix.Set(v.row, v.col, v.value)

		if !reflect.DeepEqual(v.matrix, v.Expected) && v.ExpectedOutput == output {
			t.Error(k, *v.Expected, *v.matrix, v.ExpectedOutput, output)
		}
	}
}
