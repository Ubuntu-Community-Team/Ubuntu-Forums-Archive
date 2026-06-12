---
title: "Getting under way ..."
date: 2009-07-28
forum: New to Ubuntu
---

### Post by m-v-p on 2009-07-28
Hello.
   
  I have been considering switching completely to Linux - Ubuntu for quite some time and giving Windows the right kick it deserves for being the imperialists they are. Now the time has come as I am about to buy a new computer, starting from a "barebone" - so on the harddisk I put in, there won't even be a trace of Windows at all.
  I have however a few questions :
  
[LIST=1]
[*]Do I have complete access to all the files on my computer ? I mean can I run DOS 6.0 ?
[*]Does Ubuntu also keep such annoying ".dat" alike files that you can not delete and that store everything you do on your machine ? (actually I can delete Windows .DAT files, but it takes some effort 8))
[*]However annoying, I would have to be able to run some of my Windows programs. I read that Wine is the solution for that, but do programs have to be installed under Windows first ? Do all Windows programs run with Wine ? As I am not planning to install Windows at all, this would be a real problem.
[*]If the need should arise, can I add Windows without having to go through a complete Ubuntu installation again. I fear that Windows would claim drive C: all for itself and mess everything up that is already there.
[/LIST]
          Greetings,
   
  Michel Van Passel

---

### Post by lisati on 2009-07-28
> **m-v-p said:**
> Hello.
   
  I have been considering switching completely to Linux - Ubuntu for quite some time and giving Windows the right kick it deserves for being the imperialists they are. Now the time has come as I am about to buy a new computer, starting from a "barebone" - so on the harddisk I put in, there won't even be a trace of Windows at all.
  I have however a few questions :
  
[LIST=1]
[*]Do I have complete access to all the files on my computer ? I mean can I run DOS 6.0 ?
[*]Does Ubuntu also keep such annoying ".dat" alike files that you can not delete and that store everything you do on your machine ? (actually I can delete Windows .DAT files, but it takes some effort 8))
[*]However annoying, I would have to be able to run some of my Windows programs. I read that Wine is the solution for that, but do programs have to be installed under Windows first ? Do all Windows programs run with Wine ? As I am not planning to install Windows at all, this would be a real problem.
[*]If the need should arise, can I add Windows without having to go through a complete Ubuntu installation again. I fear that Windows would claim drive C: all for itself and mess everything up that is already there.
[/LIST]
          Greetings,
   
  Michel Van Passel
1. There is an "add-on" for Ubuntu, sometimes called "dosbox" and sometimes called "dosemu" that will let you run DOS programs. If memory serves correctly, it is based on [http://www.freedos.org/](http://www.freedos.org/)
2. Not to the same extent: Ubuntu organizes its files differently
3. Wine can run *some* but **not** all Windows software. Some information can be found at [http://www.winehq.org/](http://www.winehq.org/)
4. I'd suggest setting your system up as a "dual boot" while you're finding your way around Ubuntu. For more information, have a look here: [https://help.ubuntu.com/9.04/switching/dualboot.html](https://help.ubuntu.com/9.04/switching/dualboot.html)

---

### Post by nhasian on 2009-07-28
it is easier to install windows first, and then ubuntu 2nd.  just make sure during the installer that you partition the hard disk to leave room for ubuntu.

---

### Post by MelDJ on 2009-07-28
i would suggest installing ubuntu for daily use and installing windows on virtualbox for games etc.

---

### Post by QIII on 2009-07-28
> **m-v-p said:**
> Hello.
   
  I have been considering switching completely to Linux - Ubuntu for quite some time and giving Windows the right kick it deserves for being the imperialists they are. Now the time has come as I am about to buy a new computer, starting from a "barebone" - so on the harddisk I put in, there won't even be a trace of Windows at all.
  I have however a few questions :
  
[LIST=1]
[*]Do I have complete access to all the files on my computer ? I mean can I run DOS 6.0 ?
[*]Does Ubuntu also keep such annoying ".dat" alike files that you can not delete and that store everything you do on your machine ? (actually I can delete Windows .DAT files, but it takes some effort 8))
[*]However annoying, I would have to be able to run some of my Windows programs. I read that Wine is the solution for that, but do programs have to be installed under Windows first ? Do all Windows programs run with Wine ? As I am not planning to install Windows at all, this would be a real problem.
[*]If the need should arise, can I add Windows without having to go through a complete Ubuntu installation again. I fear that Windows would claim drive C: all for itself and mess everything up that is already there.
[/LIST]
          Greetings,
   
  Michel Van Passel

1.  DOS, as you know it -- that is MSDOS, does not exist on a purely Linux machine.  There is a Command Line Interface, "the Terminal", that serves similar functions.  But the DOS commands you are familiar with do not work.

2.  The file structure and the sorts of file types used in the Linux operating system itself is entirely different from Windows.  You still have files like .jpg, .png, .doc, .txt available, however.

3.  Wine is limited in its ability to run some Windows programs.  As mentioned above, you can install a "sandbox" to run Windows in.

4.  See above.  By the way, the terminology "C: drive" is foreign to Linux.  I'd recommend giving the following a read to familiarize yourself with your new environment.

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by m-v-p on 2009-07-28
Of course there will be major differences, also to the terminology. So I used what I know
  I can understand that the file structure is different, but the real meaning of my question is about Linux keeping record of all the users activities as Windows does.
  But in the last couple of hours things have become rather obscure as I will point out in a new thread &#8230;
   
  Thanks for the quick replies already.

---

### Post by tarps87 on 2009-07-28
I have not noticed it to the same degree as in windows, although there is a history of commands run (something I would fine useful in windows), this can be turn off or cleared easily.
The simple answer is anything stored can be deleted, including the kernel although I really wouldn't advise this not that I have done it :-\"

---

### Post by Bradtek on 2009-07-28
Linux doesn't have a central registry 
Most apps etc will keep log files etc in their own 
directory but Linux will let you delete them.
Linux will let you delete your whole system if you tell it to.

---

