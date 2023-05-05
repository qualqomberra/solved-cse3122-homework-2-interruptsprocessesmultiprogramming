Download Link: https://assignmentchef.com/product/solved-cse3122-homework-2-interruptsprocessesmultiprogramming
<br>
In this homework you are going to develop a kernel that will support multi- programming, interrupt handling and just a bit of memory management. Please refer to your course textbook for multi-programming and study SPIM MANUAL for how SPIM architecture handles interrupts. <a href="http://pages.cs.wisc.edu/~larus/SPIM/spim_documentation.pdf">(</a><u><a href="http://pages.cs.wisc.edu/~larus/SPIM/spim_documentation.pdf">http://pages.cs.wisc.edu/~larus/SPIM/spim_documentation.pdf</a></u><a href="http://pages.cs.wisc.edu/~larus/SPIM/spim_documentation.pdf">)</a>

We have modified the SPIM packageto make it easier for your too add these functionalities. We have added a new function named void SPIM_timerHandler() that gets called every time there is a timer interrupt. The timer interrupt happens about every 100ms.

Your task is to develop a part of the kernel called SPIMOS_GTU_X.s that will perform interrupt handling, multiprogramming and context switching. Your new kernel will be loaded as an assembly file. In other words, instead of loading assembly files, you will load SPIMOS_GTU_1.s, SPIMOS_GTU_2.s, or SPIMOS_GTU_3.s

What we expect from your new OS is

<ul>

 <li>Implementing these POSIX system calls: fork, waitpid, execve, any other POSIX call that you need. These system calls will be in syscall.cpp. Do not modify any other CPP files from the SPIM package.</li>

 <li>Loading multiple programs into memory: Kernel will be able to load multiple programs into memory. This operation will be a system call.</li>

 <li>Handling multi-programming: you need to develop a <strong>Process Table </strong>that will hold the necessary information about the processes in the memory. You should study what <strong>Process Tables </strong> You can read carefully throughout the chapter 2 of the course book or any other onlineresource).</li>

 <li>Handling Interrupts: Our simulator will generate interrupts, and your kernel will handle and respond by modifying SPIM_timerHandler function in syscall.cpp</li>

 <li>Perform Round Robin scheduling: Every time a timer interrupt occurs, there is a chance to make a process switch.</li>

 <li>Whenever a context scheduling occurs, you will print all the information about the processes in process table including but not limited to the entries in the listbelow.</li>

</ul>

<ol>

 <li>ProcessID</li>

 <li>ProcessName,</li>

 <li>Programcounter</li>

 <li>Stack Pointeraddress</li>

</ol>

<strong>Life-Cycle </strong>

You will implement 3 different flavors of MicroKernel(SPIMOS_GTU_1.s, SPIMOS_GTU_2.s, and

SPIMOS_GTU_3.s). Don’t worry 90 percent of the code is same between the Micro Kernels. We further explain the details below.

When your kernel is loaded your OS  will start a process named <strong>init </strong>with <strong>process id 0. </strong>In different Micro Kernels Init process will load programs into memory differently

In the first strategy <strong>init </strong>process will initialize Process Table, load 3 different programs (listed below) to the memory start them and will enter an infinite loop until all the processes terminate.

Second strategy is randomly choosing one of the programs and loads it into memory 10 times (Same

program 10 different processes), start them and will enter an infinite loop until all the processes terminate.

Final Strategy is choosing 2 out 3 programs randomly and loading each program 3 times start them and will enter an infinite loop until all the processes terminate.

When SPIM starts, it immediately loads the <strong>MicroKernel file </strong>given by commandline parameters example EX: <strong>./</strong>spim –efexceptions.s -file SPIMOS_GTU_1.s

For every timer interrupt, <strong>OS </strong>should handle the interrupt and perform round robin scheduling.

Your programs finish execution it will acknowledge its termination by calling POSIX

<strong>PROCESS_EXIT</strong>.

Emulator will shut down only after all the programs in memory terminate.

<strong>Assembly Files </strong>

You will supply us with three different Assembly Files.

<ul>

 <li>s</li>

 <li>s</li>

</ul>

which were delivered to you with first homework, Update the System call’s.

<strong>Ex; </strong>

<strong>Input : {10, 20, 80, 30, 60, 50, 110, 100, 130, 170} x = 110; </strong>

<strong>Output : 6 </strong>

<strong> </strong>

<strong>Input : {10, 20, 80, 30, 60, 50,  110, 100, 130, 170} </strong>

<strong>x = 175; Output : -1</strong>




<ul>

 <li>asm: You are going to find collatz sequence for each number less than 25. You can find information about (Collatz conjecture on internet). For each number you will show the number being interested in, and its collatz sequence and go to next number <strong>Ex Output;</strong>7: 22 11 34 17 52 26 13 40 20 10 5 16 8 4 21</li>

</ul>




Your homework template includes several code and sample files. Here is a description for them. Do not change spim files except syscall.cpp and syscall.h and Do not send these files with your homework. Study these files to understand SPIM.




<strong> </strong>

syscall.h : sample header for SPIM OS. You can rewrite this file

syscall.cpp : sample implementation for SPIM OS. You will rewrite this file

SPIMOS_GTU_1.s, SPIMOS_GTU_2.s, and SPIMOS_GTU_3.s: OS Kernel

Flavors

LinearSearch.asm, Collatz.asm, BinarySearch.asm : Test Programs,

README : sample running instructions and report your work briefly

<strong> </strong>