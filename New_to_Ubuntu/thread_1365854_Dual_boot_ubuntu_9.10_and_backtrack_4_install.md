---
title: "Dual boot ubuntu 9.10 and backtrack 4: install"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by eeeandrew on 2009-12-27
Hi all. I've just installed ubuntu 9.10 and loving it so far. This is my 4th ubuntu install in the last 2 years and its looking great! My problem is with adding another linux distro called backtrack4 in dual boot. I have my partitions set up so that I have swap, a blank ext3, ubuntu 9.10 and my /home on the final partition. I intend to put the / partition for backtrack4 on that blank partition. 

My question is: can my /home be used by two different linux distros at the same time. Or to be a bit clearer, will setting the partition as /home for backtrack change the way ubuntu relates to it? As I understand it backtrack4 uses an kubuntu intrepid base.

I'm hoping to get this set up in time for my return to university so I can use it for my computer security class of my engineering degree, failing this I'll have to get and setup all the security tools individually.

Thanks in advance for you help,
Andrew

---

### Post by CanHasDIY on 2009-12-30
Check out [_Remote Exploit_]("http://www.remote-exploit.org/") and [_Offensive Security's_]("http://www.offensive-security.com/") site/forums. I would guess that you would need to re-partition and format the spare partition as detailed in [_this guide_]("http://www.offensive-security.com/documentation/bt4install.pdf") I found there, then modify your bootloader to include the Backtrack distro.

let me know if you get it working, I'm trying out a similar setup with BT and Ubuntu Studio:guitar:.


J.D.

---

### Post by doomdude6 on 2010-04-23
hi i was going to do the same thing with backtrack 4 final which has an installer but how would i  dual boot between them( backtrack 4 final and ubuntu 9.04) is it as simple as doing a regular install but using the leftover space from ubuntu on the hard drive and leaving a little space left for the the ''to be made'' files? i really want to do this if anybody has done this or know any info please help me i have never dual booted before so am completely new to this area of expertice and if i do this how will i choose between the 2 OS.
 
 
      thanx 
               for reading this and helping out
 
                                                        doomdude6     :P

---

### Post by 2hot6ft2 on 2010-04-23
> **doomdude6 said:**
> hi i was going to do the same thing with backtrack 4 final which has an installer but how would i  dual boot between them( backtrack 4 final and ubuntu 9.04) is it as simple as doing a regular install but using the leftover space from ubuntu on the hard drive and leaving a little space left for the the ''to be made'' files?
Yes but I would suggest using the manual partitioner option and the advanced option in the last step and clearing the box for installing the BT4 boot loader.
Then just update grub in ubuntu for BT4 to show up in grub.
If you decide to use ext4 in ubuntu BT4 will not see it but ubuntu can still see BT4 just fine.
 > **doomdude6 said:**
> i really want to do this if anybody has done this or know any info please help me i have never dual booted before so am completely new to this area of expertice and if i do this how will i choose between the 2 OS.
 
 
      thanx 
               for reading this and helping out
 
                                                        doomdude6     :P
You choose which to boot into at the grub screen.
I triple boot UUE, BT4 and Win 7 on this box and UUE and BT4 on another.
Don't ask how to use the dark side of the force. You wont get any help here or in the BT forum.

And welcome to the forum.

---

### Post by doomdude6 on 2010-04-24
thanks for the help but just one more question how to update grub or at least i its one more question for now but this is helping alot thank you so if anyone can tell me how to update grub then i should be all set
 
 
 again thanx 
doomdude6

---

### Post by 2hot6ft2 on 2010-05-01
[QUOTE=doomdude6]thanx but could u tell me a little more about how i would work the manual partitioner like should i add a new partition and could u tell me about how much space i should use i have a 140 gigabyte harddrive  althogh its listed as 160 gig and i am taking 10.1 gigs how much should i use[/QUOTE]
BT4 will be fine on 10 to 15 GB so give it a partition of at least 10 GB.
You wont be watching movies, playing music and stuff on it since you run as root all the time.

---

### Post by doomdude6 on 2010-05-01
ok thanx but should i add new partition table and is it possible to to do it using the guided option and change the space of the partitions that way or do i have to use the manual option

---

### Post by 2hot6ft2 on 2010-05-01
> **doomdude6 said:**
> ok thanx but should i add new partition table and is it possible to to do it using the guided option and change the space of the partitions that way or do i have to use the manual option
You can do it however you want. I always use the manual partitioner for more control.
If you don't already have a partition setup for it to go on then yes you'll have to create one for it.

---

### Post by doomdude6 on 2010-05-01
cool thanx
 
 
oh and sorry about not posting these questions in this thread

---

### Post by 2hot6ft2 on 2010-05-01
> **doomdude6 said:**
> cool thanx
 
 
oh and sorry about not posting these questions in this thread
No problem. Support questions should be asked in the forum so everyone benefits from it and others can give their advise as well.
You'll get the hang of it.
:guitar:

---

### Post by doomdude6 on 2010-05-01
hi i installed it and then went to ubuntu and updated grub using the command sudo update-grub then restarted and went to  the grub menu and the only options were ubuntu 9.04 there was nothing else can somebody tell me why and maybe tell me what else i can do 
 
 
thanx

---

