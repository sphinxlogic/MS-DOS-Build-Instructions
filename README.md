How to Build MS-DOS and the Windows Operating System
				
<p><a target="_self" href="https://computerhistory.org/blog/microsoft-ms-dos-early-source-code/" data-test-app-aware-link="">MS-DOS Source</a></p>
<p>MS-DOS 1.25 was published on GitHub MS-DOS 1.25 was completely written in 8086 assembly so it needs to be assembled using an assembler (MASM and SCP 8086 Assembler). The object file(s) produced by MASM will then be linked to produce an executable which will then be converted to a raw binary executable (.COM). The .HEX files produced by SCP 8086 Assembler will be converted directly to raw .COM files using the HEX2BIN utility.</p>
<p>2. How to Make DOS?</p>

<p>This is as hard as the source code for the DOS BIOS (IO.SYS) was designed for Virtual Box and is not PC-compatible. Theoretically, the compiled binaries should work on Virtual Box but using the source code release by Microsoft alone will not produce a valid bootable disk as no source code for the boot sector is given. I do have access to the source code of the boot sector but as a result of Microsoft not releasing it publicly, I will not share it. This basically means with only the source code published by Microsoft, it is impossible to produce a working copy of MS-DOS 1.25.</p>
<p>3. What is Required</p>

<p>The following is required for compiling MS-DOS 1.25:</p>
<ul>
   <li> Microsoft Macro Assembler (MASM)</li>
   <li> Microsoft 8086 Object Linker (LINK)</li>
   <li> EXE to Binary Conversion Utility (EXE2BIN)</li>
   <li> Seattle Computer Products 8086 Assembler (ASM)</li>
   <li> HEX to Binary Conversion Utility (HEX2BIN)</li>
   <li> A copy of the MS-DOS 1.25 source code</li>
</ul>
<p>4. Details</p>

<p>The files STDDOS.ASM and MSDOS.ASM can be assembled to produce the DOS kernel and they are MASM compatible. All switches are set in the file STDDOS.ASM. MSVER generates binaries for MS-DOS with Microsoft copyright strings, IBM produces IBM PC-DOS binaries with IBM copyright strings. There is no need to change HIMEM and DSKTEST unless you want to experiment more with it.</p>

<p>COMMAND.ASM can be assembled using MASM to produce the command interpreter for MS-DOS. Just like the DOS kernel, you may use switches to produce both MS-DOS and IBM PC-DOS binaries. The HIMEM switch is also present.</p>

<p>ASM.ASM, HEX2BIN.ASM, IO.ASM and TRANS.ASM were written by SCP and must be assembled using their own assembler. IO.ASM have switches to configure the floppy disk controller and the Cromemco 4FDC is currently supported by The SIMH Altair 8800 Z80 simulator.</p>
<p>5. Compile It</p>

<p>Now, we are ready to compile MS-DOS 1.25 for the first time! If you are experienced in assembly, used those assemblers and tools listed above, then you should be able to get everything done by yourself. For those unable to assemble it on their own, my build disk will save your time.</p>

<p>Here is how to build MS-DOS 1.25 with the build disk: Download the build disk. Create a new virtual machine using your favorite emulator or hypervisor. Add a floppy drive, load the build disk. Start the virtual machine (it should boot from the build disk). Check the filenames using the DIR command and it should return: Type in MK <FILENAME> to assemble that particular component or MK ALL to assemble everything. Once you have everything assembled, type in DIR *.COM and DIR *.SYS to see the executable produced, it should be similar to: You have done it! You can now copy those executables to another disk or extract them or run them!
</p>
<p>After reading a Windows Open Source Article Mark Russivich said it wold take a rocket scientist to build Microsoft Windows and I have. I at leas thold my almatrer to that.</p>