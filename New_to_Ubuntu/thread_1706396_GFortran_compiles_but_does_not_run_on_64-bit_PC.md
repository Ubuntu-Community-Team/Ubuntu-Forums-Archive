---
title: "GFortran compiles but does not run on 64-bit PC"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by max85745 on 2011-03-13
[FONT=Courier New][SIZE=2]Hi,[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Recently I bought a new desktop PC (HP6654y, Athlon II processor, 64-bit, [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]with Windows 7) and downloaded the free GCC-GNU GFortran compiler for it,[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]from [http://quatramaran.ens.fr/~coudert/gfortran/](http://quatramaran.ens.fr/~coudert/gfortran/), following instructions[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]to the letter. After 'doing' Fortran for nearly 50 years (!!), I still[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]have a lot of stuff I need to do with it every day.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]The first dozen or so programs I tried out on this GFortran (= Fortran 2003)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]were 'small' (around 1200 ASCII characters each) and worked perfectly: they[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]compiled, linked, executed, and ran (linked) just fine. All that was needed[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]was the command 'gfortran -o xyz.f', where xyz is the name of my source[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]code file.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]But the Fortran programs I really need to run are about twenty times larger[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](25000 ASCII characters each) than those dozen trial balloons above. These[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]big programs will compile OK (no syntax or logic errors etc),but they will[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]not run. My GFortran gives me runtime errors like[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]'c:\Users\mememe\AppData\Local\Temp\ccM8j0Ey.o: xyz.f:.text+0x360a): undefined[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]reference to '_array_' ', were mememe is my administrator name, xyz is the[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]source module again, and array is the name I gave to a dimensioned character [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]array in that ASCII source file; there is also a message [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]'Collect2; Id returned 1 exit status'.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Next I experimented with inserting various link parameter combinations[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]after the -o in the above gfortran command, such as -Wextra or -Wall or -O2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]or -g or -static or -march or -libgfortran etc, all to no avail.(I am not a[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]'professional developer'.)(By the way, Gfortran, along with mingwm10.dll [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]etc etc resides in my \ProgramFiles(x86) folder.)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]I get the impression that gfortran wants some C+ modules (?), or runtime[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]libraries, or 'binaries' (?)like maybe MinGW or Cypwin or whatever. It just[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]will not TELL me what I need, where to get it, and into which folders on my[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]PC to put them. It's nerve wracking! [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Please help. [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thank you.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]'Max'[/SIZE][/FONT]

---

### Post by wep940 on 2011-03-13
Perhaps Section 6 of this can help you:
 
[http://approximatrix.com/articles/setting-up-gnu-gfortran-on-windows-xp](http://approximatrix.com/articles/setting-up-gnu-gfortran-on-windows-xp)

---

### Post by max85745 on 2011-03-14
Thanks WEP940. - I downloaded makedepf90-2.8.8.tar to a convenient directory. Then I entered my as yet empty directory \gfortran\makedepf90 and tried to "run" the following three (MSDOS command line??) commands, as Jeff Armstrong's "Step 6" suggested: ./configure  and   make   and   make install. My PC's command prompt found them totally unintelligible, rejected them. Nothing happened. \gfortran\makedepf90 is still empty and my GFortran is still stuck.

---

### Post by max85745 on 2011-03-16
Erik Toussaint enlightened me that my problem was not at runtime, but earlier. Sure enough, I had made a mistake in argument passing to a subroutine in my source code. Entirely my fault, nothing to do with any GFortran or Makedepf90 packages. I apologize for all the trouble I have caused and considered this thread totally resolved. Max85745

---

### Post by wep940 on 2011-03-16
Sorry I couldn't help you more - I haven't used Fortran since about 1976 or so.  Just glad you got it working.

---

