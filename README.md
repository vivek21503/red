from this exercise we tested how system calls work.
we need to write a system call which copies 2-D floating point matrix to another by using
kernel functions like __copy_from_user and __copy_to_user


What i did ..

first of all i go to my linux-5.19.9, after that i go to kernel and then open sys.c.
There i add a c code in which i use SYCALL_DEFINE4, which take a source  array and destination array and also 
size of array and one matrix as parameter. 4 specify no. of argument.

then i made another array and with the help of  kernel function  __copy_from_user  ,i copied elements of
 source array to new array and  then use __copy_to_user kernel function, which copy elements from new array 
 to destination array.

 on sucessful it will return 0 and sucessfully copy element from source array to destination array.
 (which is diff)



After that  i go to syscall_64.tbl and at no 451, i write 451 common TWODMATRIX_SYSTEM_Call sys_matrix
After that i compile the kernel with name _hocus_pocus_2.

after that i  came back to my linux directory and then made a folder in which i made a mat.c.


There i used #define TWODMATRIX_SYSCALL 451
451 sepecify the position in where i add in syscall_64.tbl.
in main i made source array which has floating elements amd destination elements which is empty.
After use of function syscall, kernel function copy elements from source array to destination array
we also check for (sys_call_status !=EFAULT).
