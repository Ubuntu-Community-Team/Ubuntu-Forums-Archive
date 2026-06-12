---
title: "can't boot"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-12-26
I have an older desktop that was running 10.10 fine then it stopped booting.I have a separate home partition so wanted to just reinstall but CD hangs at first forward prompt. I can get into the live CD but then gparted won't open to reformat /. Are there any other options?Thank you.

---

### Post by fooman on 2010-12-26
if you can boot to the desktop of the live cd....just click the "install" icon on the desktop,  then follow the prompts till you get to the partitioning screen.

once there,  you can choose to "create partitions manually" (not sure of the exact wording,  but you will see a similar choice)....pick that,  and you can delete/create/format whichever partitions you choose.

hope that helps.

---

### Post by Gone fishing on 2010-12-26
Bad CD? burn another from the iso?

---

### Post by amjjawad on 2010-12-26
> **cmcanulty said:**
> I have an older desktop that was running 10.10 fine then it stopped booting.I have a separate home partition so wanted to just reinstall but CD hangs at first forward prompt. I can get into the live CD but then gparted won't open to reformat /. Are there any other options?Thank you.

1) How did your machine stop booting? can't you login to Ubuntu at all?

2) Do you have another OS on that machine?

3) Have you checked MD5SUM before you burn the CD? on my signature, there's all the info you need (check step1 link).

4) Did you burn at the lowest speed say 16x?

5) Does your machine support booting from USB? if yes, try to create LiveUSB.
Here's howto: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

or try: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by cmcanulty on 2010-12-26
1 yes just got the black screen with Dell logo
2 no
3 yes
4 burned at 4x CD will let me run live but not install so how can I run gparted and fix the /partition? I have a separate /Home when I try to open gparted on live CD from admin menu nothing opens
5 no it's old no boot from USB
6 I tried install from desktop icon in live CD and still hangs on 1st forward prompt
Thanks all

---

### Post by amjjawad on 2010-12-26
> **cmcanulty said:**
> 1 yes just got the black screen with Dell logo
2 no
3 yes
4 burned at 4x CD will let me run live but not install so how can I run gparted and fix the /partition? I have a separate /Home when I try to open gparted on live CD from admin menu nothing opens
5 no it's old no boot from USB
6 I tried install from desktop icon in live CD and still hangs on 1st forward prompt
Thanks all

So you can get the desktop of the LiveCD but the installation will hung on the 
first forward, eh?

Ok, how much RAM do you have?

---

### Post by sandyd on 2010-12-26
have you run memtest?

---

### Post by cmcanulty on 2010-12-26
512 MB ram. Yes install hangs on first forward prompt whether from install or live CD then install from desktop. Maverick worked fine until a week ago on it.

---

### Post by cmcanulty on 2010-12-26
no what would that show? I tries it with my laptop and got
```

cmcanulty@Gateway:~$ memtest
memtest: command not found
cmcanulty@Gateway:~$
```

---

### Post by amjjawad on 2010-12-26
> **cmcanulty said:**
> 512 MB ram. Yes install hangs on first forward prompt whether from install or live CD then install from desktop. Maverick worked fine until a week ago on it.

512MB but do you share some with your Graphics Memory? I mean some Motherboards have built-in Graphics Card and you need to share some of your RAM with it (Shared Memory) and that's an option in BIOS.

I can share up to 256MB from my RAM which is 512MB too. When I did 50:50 the LiveCD couldn't load the whole desktop. I was just testing.

You're trying with 10.10. Try 10.04.

---

### Post by amjjawad on 2010-12-26
> **cmcanulty said:**
> no what would that show? I tries it with my laptop and got
```

cmcanulty@Gateway:~$ memtest
memtest: command not found
cmcanulty@Gateway:~$
```

Not from Terminal. You need to run that while you're booting from the LiveCD.

[B]Select Test Memory (forget the red cursor :) )
[/B]
[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132[/IMG]

---

