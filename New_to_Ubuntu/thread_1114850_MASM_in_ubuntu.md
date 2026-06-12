---
title: "MASM in ubuntu"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by manuganji on 2009-04-03
I need an equivalent of MASM (Macro Assembler) in windows for ubuntu . Just MASM not TASM,NASM or something else. Please help me with this. I need it for one of my courses. I really don't want to install windows again for this. Thanks a lot in advance.

---

### Post by Werewolf85 on 2009-04-03
> **manuganji said:**
> I need an equivalent of MASM in windows for ubuntu . Just MASM not TASM,NASM or something else. Please help me with this. I need it for one of my courses. I really don't want to install windows again for this.

If you just want to use it for academic purposes i guess it would work under Wine: [http://winehq.org]("http://winehq.org"). I've read something about violating the MASM EULA when developing on Open Source Software, haven't read it myself though. But you should take that under consideration.

If Wine doesn't do the trick you may install Windows in a Virtual Machine using VMware Server: [http://www.vmware.com/products/server/]("http://www.vmware.com/products/server/")

Hope this will help!

---

### Post by mvalviar on 2009-04-03
NASM is in the repos.

---

### Post by kellemes on 2009-04-03
> **manuganji said:**
> I really don't want to install windows again for this.

You have to..
Use a vm like VirtualBox.

---

### Post by lkraemer on 2009-04-03
I don't know what you are exactly trying to do with MASM, but since MASM
was DOS based why can't you use DOSBOX, and run MASM from DOSBOX.  It would
be the same as using an old DOS based box.  DOS box should be in the repos.

It would be worth a try.

You might consider A86 (Assembler) and D86 (Dis-assembler) while you are
playing with MASM.  They used to be very good programs.  I did use them
years ago, but have forgotten most of that now.

If you can't locate A86 or D86 PM me as I have them somewhere, on an old DOS drive.

Also, a search of this forum talks about DOSBOX-FE a Front End for DOSBOX.
It might be worth trying.
[http://ubuntuforums.org/showthread.php?t=853174&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=853174&highlight=dosbox)

Seems to be an issue with keymapping:
[http://ubuntuforums.org/showthread.php?t=1021781&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=1021781&highlight=dosbox)

Search forum for dosbox for more details.

Good Luck.

lkraemer

---

### Post by lkraemer on 2009-04-03
Yes, MASM51 works fine in the DosBox window.  I couldn't find a
copy of one of my old assembler programs, but I did try
to use MASM.  WOW!  It has been years, since I did that kind
of work.  But it is FAST, COMPACT, and works good if you code
it correctly.  I prefered using TASM because of the TDEBUGGER
that was out.  It was NICE!  Symbolic Debugger by Borland Intl.

Anyway, just go to your /home/login directory, create a dosprog
subdirectory and you will be all set.  I made another for MASM
at /home/login/dosprog/masm51

I also changed the permissions for both to login:login versus root.
Then in DosBox you follow the screen prompts.  (Note: If you open
DosBox before you create the MASM51 subdirectory you will have to exit
and start DosBox again so it finds the subdirectories.)

You should be in good shape for your class!  Wish I was going.......

(I wrote a small asm program to turn the NUMLOCK key off in 7 bytes.
Another guy wrote it in "C" and it was 32K.  He was impressed.)

lkraemer

---

### Post by manuganji on 2009-04-04
I'd like to thank all those who have responded so far. BTW.... Can you please give me solutions which DON'T require me to use WINE or VMware. Is there no other clean and promising method?? And.. **lkraemer** how could you do that in seven bytes ?!!!!!! :o

---

### Post by pg-13(prostitute) on 2009-04-04
i use amd chips so im fond of at&t syntax

seems wrong to use intel

---

### Post by lkraemer on 2009-04-04
manuganji,
Well, after searching some old backup CD's I found the numlock.com
program......and I was wrong......it was 8 bytes not 7.  I won't be
able to get to my source for another 3 weeks. I'll send it to you
to view when I find it.

In the mean time, I wrote another program that logged each powerup
of a friends work computer so he could tell what time, and how many
times it had been powered up while he was gone.  He disguised it as
a video driver being loaded.

```

;=============================================================================
                DOSSEG
                .MODEL TINY
                .CODE
                ORG     0100h       ;this is a COM file
start:
                jmp     start2      ;jump over local data
;----------------------------------------------------------
; Declare the 32 bytes to be evaluated here...
;----------------------------------------------------------
            DB    13 DUP (0)

BITES       DB    40h               ;original data to test for serial
            DB    41h               ;number - located at 110
            DB    42h
            DB    43h
            DB    44h
            DB    45h
            DB    46h
            DB    47h
            DB    48h
            DB    49h
            DB    50h
            DB    51h
            DB    52h
            DB    53h
            DB    54h
            DB    55h
            DB    56h
            DB    57h
            DB    58h
            DB    59h
            DB    60h
            DB    61h
            DB    62h
            DB    63h
            DB    64h
            DB    65h
            DB    66h
            DB    67h
            DB    68h
            DB    69h
            DB    70h
            DB    71h



DATA0       DB    32 DUP (0)        ;first set is NOT so look at it -130

DATA1       DB    32 DUP (1)        ;rotated data one bit      - 150
DATA2       DB    32 DUP (2)        ;rotated data two bits     - 170
DATA3       DB    32 DUP (3)        ;rotated data three bits   - 190
DATA4       DB    32 DUP (4)        ;rotated data four bits    - 1B0
DATA5       DB    32 DUP (5)        ;rotated data five bits    - 1D0
DATA6       DB    32 DUP (6)        ;rotated data six bits     - 1F0
DATA7       DB    32 DUP (7)        ;rotated data seven bits   - 210
DATA8       DB    32 DUP (8)        ;rotated data eitht bits   - 230
JUNK        DB    32 DUP (255)      ;end of area to inspect    - 250
NUMBYTES    DW    32                ;32 data values

;=============================================================================
;----------------------------------------------------------
; Declare additional functions here...
;----------------------------------------------------------

; ---------------------------------------------------------------------
; This routine zeros the data areas.
; Entry: DI=destination  CX=bytes to zero  AX=0
; Exit: returns
; ---------------------------------------------------------------------
zerodata     PROC    NEAR
             xor     al, al              ;zero register
             mov     cx, [NUMBYTES]      ;do for 32 bytes
             cld                         ;increment
             rep stosb
             RET
zerodata     ENDP

; ---------------------------------------------------------------------
; This routine does a NOT on each byte then stores it in DATA 0.
; Entry: CX=number of bytes  SI=source  DATA1=destination
; Exit: returns
; ---------------------------------------------------------------------
PNOT         PROC    NEAR
donot:
             lodsb                       ;get byte pointed to by SI
             not     al                  ;invert all bits
             stosb                       ;store them for now
             loop    donot               ;do all 32 bytes
             RET
PNOT         ENDP

; ---------------------------------------------------------------------
; This routine rotates each byte left by one bit.
; Entry: CX=number of bytes  SI=source  DATA1 thru 8=destination
; Exit: returns
; ---------------------------------------------------------------------
PROL        PROC    NEAR
dorol:
            lodsb                        ;get byte pointed to by SI
            rol     al,1                 ;invert all bits
            stosb                        ;store them for now
            loop    dorol                ;do all 32 bytes
            RET
PROL        ENDP


start2:
;----------------------------------------------------------
; Code for MAIN goes here...
;----------------------------------------------------------
                push    cs                  ;make CS=DS=ES
                push    cs
                pop     ds
                pop     es
;               mov     cx, [NUMBYTES]
;               mov     di, offset DATA0    ;zero data area 0
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA1     ;zero data area 1
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA2     ;zero data area 2
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA3     ;zero data area 3
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA4     ;zero data area 4
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA5     ;zero data area 5
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA6     ;zero data area 6
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA7     ;zero data area 7
;               call    zerodata

;               mov     cx, [NUMBYTES]
;               mov     di,offset DATA8     ;zero data area 8
;               call    zerodata


                mov     cx, [NUMBYTES]      ;try NOT data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA0    ;destination
                call    pnot                ;NOT all bits

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA1    ;destination
                call    prol                ;TIMES 1   BIT 1

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA2    ;destination
                call    prol                ;TIMES 2   BIT 2

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA3    ;destination
                call    prol                ;TIMES 4   BIT 3

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA4    ;destination
                call    prol                ;TIMES 8   BIT 4

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA5    ;destination
                call    prol                ;TIMES 16  BIT 5

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA6    ;destination
                call    prol                ;TIMES 32  BIT 6

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA7    ;destination
                call    prol                ;TIMES 64  BIT 7

                mov     cx, [NUMBYTES]      ;try shift left data bytes
                mov     si, offset BITES    ;source
                mov     di, offset DATA8    ;destination
                call    prol                ;TIMES 128 BIT 8


                mov     ah,04ch             ;normal exit
                mov     al,0
                int     21h

                END     start


```
and here was the batch file to assemble/link it.

```

erase logpwrup.com

erase logpwrup.exe

erase logpwrup.bak

d:\turboc\tasm /zi logpwrup

d:\turboc\tlink /v /l /x logpwrup

td logpwrup

```
As you can tell I used tasm versus MASM, but they worked the same.

Now you can play.

Documentation:
```
  
                           LOGPWRUP


PURPOSE:     LOGPWRUP will save the DATE and TIME of system power up
             in a text file that is specified from the command line.
             This file can be placed anywhere on your hard disk as
             long as the specified path exists.

LOADING:     Run LOGPWRUP from within your AUTOEXEC.BAT file to store
             SYSTEM RESETS or POWER UP conditions.

             LOGPWRUP C:\PATHA\PATHB\PATHC\POWERUP.LOG

             DATE and TIME will be saved to Drive C, PathA,
             PathB, PATHC in POWERUP.LOG

             If you want to get sneaky and try to disguise what this
             program is doing just rename the LOGPWRUP.EXE file to
             SETVIDEO.COM and use the following command within your
             AUTOEXEC.BAT file.

             SETVIDEO C:\PATHA\PATHB\PATHC\EGA.DRV

             Most folks will assume that an EGA Driver is being loaded
             by not knowing what the program really does.

             NOTE:  LOGPWRUP will not create any subdirectories on
                    your drive, so they must exist when the program
                    is executed.  It will not log any WARM BOOTS, but
                    can be easily modified to log these if they are
                    needed.

```

lkraemer

---

### Post by lkraemer on 2009-04-09
manuganji,
Here is a link to some of the PC Magazine Assembly Downloads.

[http://shareware.pcmag.com/category.php%5Baction%5Dbrowse&i=0&id=16&f=||||&s=product.date_released|DESC%5BSiteID%5Dpcmag](http://shareware.pcmag.com/category.php%5Baction%5Dbrowse&i=0&id=16&f=||||&s=product.date_released|DESC%5BSiteID%5Dpcmag)

lkraemer

---

### Post by manuganji on 2009-04-14
thnx a lot lkramer.

---

### Post by ppjdee on 2013-04-27
I do believe this is considered necro lol. I would start a new thread about your problem, since this will be closed in a few mins.

---

### Post by wildmanne39 on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

