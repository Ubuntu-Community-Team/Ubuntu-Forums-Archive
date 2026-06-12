---
title: "building a kernel to boot from a floppy please help"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by voncloft on 2009-04-18
i am not sure if this is the right place to ask about building a kernel but here it goes, i have been trying to compile a kernel for the past 2 days to boot from a floppy , i did manage to write a .asm file to a floppy and boot a bootloader but i want to take it a step further and boot a bin file created from .c and .h files NOT CPP thats all anybody talks about on google which are converted to .o files.

below are the files that i have downloaded from the internet just to see how an os works i do everything the .bat file says to do by hand in a terminal (i'm in ubuntu 8.1 and the kernel version of the ubuntu is 2.6.29-ultimate and don't know how to run .bat files)  when i compile with "ld -T kernel.ld kernel.o k_entry.o" without quotes it says "undefined references" in the main to _k_main.

Can someone please point me in the right direction on this i would like to create a simple os just to understand how an os works and its "supposed" to be fun but so far i'm pulling my hair out (not literally of course but you get the idea). 

if i posted in the wrong place would somebody let me know

==========k_defines.h=================
#define WHITE_TXT 0x7

#define BLUE_TXT 0x09



#define UCHAR unsigned char

#define USHORT unsigned short



===========k_entry.asm=============
[BITS 32]



[global start]

[extern _k_main] ; this is in the c file



start:

  ; stop using bootloader GDT, and load new GDT

  lgdt [gdt_ptr]



  mov ax,LINEAR_DATA_SEL

  mov ds,ax

  mov es,ax

  mov ss,ax

  mov fs,ax

  mov gs,ax



  call _k_main



  jmp $ ; crash



;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;



SECTION .data



gdt:

; NULL descriptor

	dw 0		; limit 15:0

	dw 0		; base 15:0

	db 0		; base 23:16

	db 0		; type

	db 0		; limit 19:16, flags

	db 0		; base 31:24



; unused descriptor

	dw 0

	dw 0

	db 0

	db 0

	db 0

	db 0



LINEAR_DATA_SEL	equ	$-gdt

	dw 0FFFFh

	dw 0

	db 0

	db 92h		; present, ring 0, data, expand-up, writable

	db 0CFh		; page-granular (4 gig limit), 32-bit

	db 0



LINEAR_CODE_SEL	equ	$-gdt

	dw 0FFFFh

	dw 0

	db 0

	db 9Ah		; present,ring 0,code,non-conforming,readable

	db 0CFh		; page-granular (4 gig limit), 32-bit

	db 0

gdt_end:



gdt_ptr:

	dw gdt_end - gdt - 1

	dd gdt

========================kernel.c===================
#include "k_defines.h"



inline void outportb(unsigned int port,unsigned char value);



unsigned int panic(char *message);



void k_clear_screen();

unsigned int k_printf(char *message, unsigned int line);

void update_cursor(int row, int col);



k_main() // like main

{

	k_clear_screen();



	k_printf("Welcome to Simplified OS.", 0);

	update_cursor(1, 0);

	k_printf("Right now the kernel is loaded at 1MB physical,/nbut mapped at FF800000 hex.", 3);

	update_cursor(5, 0);

};



void k_clear_screen() // clear the entire text screen

{

	char *vidmem = (char *) 0xb8000;

	unsigned int i=0;

	while(i<(80*2*25))

	{

		vidmem[i]=' ';

		i++;

		vidmem[i]=WHITE_TXT;

		i++;

	};

};



unsigned int k_printf(char *message, unsigned int line)

{

	char *vidmem = (char *) 0xb8000;

	unsigned int i=0;



	i=(line*80*2);



	while(*message!=0) // 24h

	{

		if(*message==0x2F)

		{

			*message++;

			if(*message==0x6e)

			{

				line++;

				i=(line*80*2);

				*message++;

				if(*message==0)

				{

					return(1);

				};

			};

		};

		vidmem[i]=*message;

		*message++;

		i++;

		vidmem[i]=0x7;

		i++;

	};



	return(1);

};



/* ==============  */



inline void outportb(unsigned int port,unsigned char value)  // Output a byte to a port

{

    asm volatile ("outb %%al,%%dx"::"d" (port), "a" (value));

};



/* ==============  */



/* by DF */

void update_cursor(int row, int col)

{

	USHORT	position=(row*80) + col;

	// cursor LOW port to vga INDEX register

	outportb(0x3D4, 0x0F);

	outportb(0x3D5, (UCHAR)(position&0xFF));

	// cursor HIGH port to vga INDEX register

	outportb(0x3D4, 0x0E);

	outportb(0x3D5, (UCHAR)((position>>8)&0xFF));

};



unsigned int panic(char *message) // just a modified version of k_printf

{

	char *vidmem = (char *) 0xb8000;

	unsigned int i=0;

	unsigned int line=0;



	i=(line*80*2);



	while(*message!=0) // 24h

	{

		if(*message==0x2F)

		{

			*message++;

			if(*message==0x6e)

			{

				line++;

				i=(line*80*2);

				*message++;

				if(*message==0)

				{

					return(1);

				};

			};

		};

		vidmem[i]=*message;

		*message++;

		i++;

		vidmem[i]=0x9; // use blue text

		i++;

	};

	return(1);

};


==========================kernel.ld=====================
OUTPUT_FORMAT("binary")

ENTRY(start)

SECTIONS

{

  .text  0xFF800000 : {

    *(.text)

  }

  .data  : {

    *(.data)

  }

  .bss  :

  { 					

    *(.bss)

  }

}


===============kernelbuild.bat=========================
gcc -c kernel.c -o kernel.o

nasm -f aout k_entry.asm -o k_entry.o

ld -T kernel.ld kernel.o k_entry.o

rename a.out kernel.bin

---

### Post by EnglishSparrow on 2009-04-18
You should be able to build it with

```

gcc -c

```
If you've wrote your script/kernel in C. .asm is assembly correct? Good job. 

kbuild.bat I think has wrong extension. .bat is windows batch file.

EDIT: Rename kbuild.bat to kbuild.sh and make the file look like this:

```

#!/bin/bash

gcc -c kernel.c -o kernel.o

nasm -f aout k_entry.asm -o k_entry.o

ld -T kernel.ld kernel.o k_entry.o

rename a.out kernel.bin

```

Then give kbuild.sh full read/write permissions to your user and make it executable.

---

### Post by voncloft on 2009-04-19
thank you for the good job, ive been workin with linux for 3 yrs and i still prefer it over windows.

i tried what you said with the 2 code snips given.
gcc -c

and rewrote the .bat file to compile it to a .sh file.

=========results of what was said to try
create
============build.sh - renamed from the .bat file ================
#!/bin/bash

gcc -c kernel.c -o kernel.o

nasm -f aout k_entry.asm -o k_entry.o

ld -T kernel.ld kernel.o k_entry.o

rename a.out kernel.bin
======================

ran sudo sh build.sh
got error:

k_entry.o:k_entry.o:(.text+0x16): undefined reference to `_k_main'
Bareword "a" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "out" not allowed while "strict subs" in use at (eval 1) line 1.
still experiencing errors. 


My question: how do i compile the "gcc -c" with what files annd how, could you explain a bit more in depth of how to compile with just gcc -c?

Files trying to work with in the future:
Here is what my bootstraploader looks like now: it is subject to change when i know  how to load asm files in asm or other types of machine code in asm but right now it just boots and stops.

=============bootloader.asm======================
    [ORG 7C00h]                   
    ; ---------------------------------------------------------
    ; Main program
    ; ---------------------------------------------------------

    ;some how load an asm or machine file

    times 512-($-$$)-2 db 0
            dw 0AA55h

thanks in advance. :D

---

