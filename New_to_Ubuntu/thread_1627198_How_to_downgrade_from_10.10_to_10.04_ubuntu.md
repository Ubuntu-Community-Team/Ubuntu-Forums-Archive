---
title: "How to downgrade from 10.10 to 10.04 ubuntu"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by blancoisgod on 2010-11-21
How do i do it? i dont have any windows partitions, and i want to completely get rid of 10.10 and run 10.04. Im using 64 bit, if that helps

---

### Post by howefield on 2010-11-21
There is no downgrade process, you are looking at backing up your valuable data, and reinstalling 10.04.1 afresh.

---

### Post by blancoisgod on 2010-11-21
alright, i dont want to back up any precious data(i dont have pics or any programs i need to save)

How would i do it?

---

### Post by CharlesA on 2010-11-21
If you don't have anything to backup, then just boot off the 10.04 cd and install it over the 10.10 install.

---

### Post by blancoisgod on 2010-11-21
thats the problem.

I boot into the cd and i get a screen full of texts. I have tried multiple copies and they all do the same.

I have a toshiba Sattelite A505

---

### Post by CharlesA on 2010-11-21
What does the text say?

Did you verify the MD5SUM of the ISO before burning it to a cd?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by blancoisgod on 2010-11-21
The text is really weird. The last line looks like this

? Child_rip+0x0/0x20

---

### Post by howefield on 2010-11-21
Browse this thread and maybe the link in it 

[http://ubuntuforums.org/showthread.php?t=1496796](http://ubuntuforums.org/showthread.php?t=1496796)

---

### Post by blancoisgod on 2010-11-21
ok it wont let me run the .exe to update the BIOS

---

### Post by CharlesA on 2010-11-21
You could try running it in Wine, but I'd suggest running it on a Windows box.

---

### Post by blancoisgod on 2010-11-21
jeez, i am such a noob at this.

Ok, is wine already on 10.10 or am i gonna have to download it?

---

### Post by CharlesA on 2010-11-21
You'd have to install it.

Aren't there instructions on how to update the BIOS if you aren't running Windows on the toshiba website?

---

### Post by blancoisgod on 2010-11-21
i dont see it. Am I missing something?

---

### Post by CharlesA on 2010-11-21
Why do you need to update the BIOS in the first place?

---

### Post by blancoisgod on 2010-11-21
because according to that link provided, i need to update my BIOS in order to boot Lucid Lynx

---

### Post by tekkidd on 2010-11-21
The only way to downgrade is to do a fresh install. For your next install consider installing /home on a seperate partition so if you do need to format/rensitall data backup wont be a problem

---

### Post by blancoisgod on 2010-11-21
@tekkid
thats what i am trying to do. When I run the cd, itgives me a line of text.

Im going to install the update for my BIOS. Let me see if that does it

---

### Post by blancoisgod on 2010-11-21
alright, installed BIOS update from a cd(like it said to do) and still no dice.

I still get that funky code of text thats all over my screen.

---

### Post by CharlesA on 2010-11-23
Don't really have any more ideas. Maybe try the 32-bit version and see if it gives you the same error?

---

### Post by blancoisgod on 2010-11-23
Alright, I tried everything. Nothing will work.

It is ok though, because alot of the compatibility issues i were having(like flash and the android sdk) work now.

This was actually unnecessary for me, but it might help someone else. Thinks for yall's time though :)

---

