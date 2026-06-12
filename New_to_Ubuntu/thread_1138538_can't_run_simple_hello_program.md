---
title: "can't run simple hello program"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Ubunser on 2009-04-26
I thought I should at least try to figure out how a processor(x86) works and according to an Assembly tutorial my first program is helloworld.
I have NASM and probably have ld. 
So I created hello.asm ---then---hello.o---then---hello---
The final one is what the problem about. It should be executable, but when I click twice no massage no nothing. I don't know what is its extention. The emblem(not sure if this is suitable word) of the file is blue with two gears.
Thanks in advance

---

### Post by linuxuser21 on 2009-04-26
You probably made a *Windows* executable.  Linux cannot execute .exe files navively.  You need an app called [Wine]("http://www.winehq.org") to run Windows programs.

---

### Post by Ubunser on 2009-04-26
Ok, how can I prevent creating Windows executable files?

---

### Post by linuxuser21 on 2009-04-26
If I understand correctly, you are using a program or instructions to make executables?  In this case, the program or instructions you are using is for Windows.  You would need to find an application that does the same thing, only in Linux.  However, I would still try Wine.  It will run it and I'm sure you'll find it useful down the road later as well.

---

### Post by unutbu on 2009-04-26
nasm and ld are GNU/Linux tools which will produce Linux compatible executables. See

[http://en.kioskea.net/faq/sujet-1559-compiling-an-assembly-program-with-nasm#with-linux](http://en.kioskea.net/faq/sujet-1559-compiling-an-assembly-program-with-nasm#with-linux)

---

### Post by Ubunser on 2009-04-26
See, I already have and use wine for some applications. But I think in this case I should do without it. I've written my first program using free ubuntu friendly NASM and some ld. I think Windows has nothing to do with what I'm programming on Ubuntu. 
But I'm really new to Ubuntu and programming and might be wrong. But I'm sure I'm not using any Windows-oriented software.

---

### Post by ddrichardson on 2009-04-26
I think you're asking how to set it to executable```
chmod +x hello
```

---

### Post by Slim Odds on 2009-04-26
What does this program do? Can we see some source?

It's likely that the programs sends its output to the console, which you wouldn't see if you launch it using the "double click" method from the GUI.

You need to open a terminal and run it from there.

---

### Post by Ubunser on 2009-04-26
I think it should display message HelloWorld

[B]section .text				;section declaration

			;we must export the entry point to the ELF linker or
    global _start	;loader. They conventionally recognize _start as their
			;entry point. Use ld -e foo to override the default.

_start:

;write our string to stdout

        mov     edx,len ;third argument: message length
        mov     ecx,msg ;second argument: pointer to message to write
        mov     ebx,1   ;first argument: file handle (stdout)
        mov     eax,4   ;system call number (sys_write)
        int     0x80	;call kernel

;and exit

	mov	ebx,0	;first syscall argument: exit code
        mov     eax,1   ;system call number (sys_exit)
        int     0x80	;call kernel

section .data				;section declaration

msg     db      "Hello, world!",0xa	;our dear string
len     equ     $ - msg                 ;length of our dear string
[/B]

Also I tried to execute it by typing "hello" in the terminale but didin't work. This is a wrong way to execute, wright?

---

### Post by linuxuser21 on 2009-04-26
> **unutbu said:**
> nasm and ld are GNU/Linux tools which will produce Linux compatible executables. See

[http://en.kioskea.net/faq/sujet-1559-compiling-an-assembly-program-with-nasm#with-linux](http://en.kioskea.net/faq/sujet-1559-compiling-an-assembly-program-with-nasm#with-linux)

Oh, I see.  I haven't used that before so I didn't know.  lol.

---

### Post by ddrichardson on 2009-04-26
Once its compiled it should run, otherwise set it to execute by typing chmod +x hello

---

### Post by unutbu on 2009-04-26
```
nasm -f elf hello.asm 
ld hello.o -o hello
./hello
```
Returns
```
Hello, world!
```

---

### Post by Slim Odds on 2009-04-26
> **unutbu said:**
> ```
nasm -f elf hello.asm 
ld hello.o -o hello
./hello
```Returns
```
Hello, world!
```

Or use this for 64 bit:```
nasm -f [COLOR=Red]elf64[/COLOR] hello.asm 
ld hello.o -o hello
./hello
```

---

### Post by Ubunser on 2009-04-26
Thanks Unutbu, after ./hello it replied "Hello, World!". I thought it will appear in GUI, lol. I'm learning, thanks guys for spending time on newbie like me.

---

### Post by Ubunser on 2009-04-26
> **Slim Odds said:**
> Or use this for 64 bit:```
nasm -f [COLOR=Red]elf64[/COLOR] hello.asm 
ld hello.o -o hello
./hello
```

I have 32-bit processor and Ubuntu, but thanks anyway:)

---

