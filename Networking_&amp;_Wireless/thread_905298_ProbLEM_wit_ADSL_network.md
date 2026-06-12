---
title: "ProbLEM wit ADSL network"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Coonstantine on 2008-08-30
hello , i cant speak english very well but i try get some help from english forum cos i live in uk . i installed already ubuntu 8.04 and in administration > network > is nothing dont have internet .. i was trying use ubudsl program but i need build-essential .. i saw here topic about it 
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v 

but console show me : failed to mount the cdrom
please for fast help ! ;(

---

### Post by kagashe on 2008-08-30
> **Coonstantine said:**
> hello , i cant speak english very well but i try get some help from english forum cos i live in uk . i installed already ubuntu 8.04 and in administration > network > is nothing dont have internet .. i was trying use ubudsl program but i need build-essential .. i saw here topic about it 
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v 

but console show me : failed to mount the cdrom
please for fast help ! ;(
If you are putting the CD in the drive and entering the command:
> @ sudo apt-cdrom add
This command will unmount the CD and ask you to insert the CD once again.

It will be better if you enter the command without putting any CD in the drive. You will get a prompt to insert the CD and press enter. Do it.

If the CD is already inside take it out and put it once again.

kagashe

---

