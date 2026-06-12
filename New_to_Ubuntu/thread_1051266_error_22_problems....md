---
title: "error 22 problems..."
date: 2009-01-26
forum: New to Ubuntu
---

### Post by deathscith on 2009-01-26
alright, so i started with windows vista 64 bit on a gateway pc, it has 3 harddrives in it, two raided 320gb's and an added 500gb, i partitioned the 500gb harddrive while installing ubunto 8.10 x64, after that, all i got was a error 22 on booting up and am now using the live disk to ask for help/ try and fix it, ive looked around and people say use the console to do 

sudo grub
find /grub/stage=1 

or many other varients of that, but all i get is an error 15 and it says it cant find any parts, i also did a method on here that rewrote my mbr to boot windows, so i can get into my windows now, but the networks all messed on it so i cant get to the internet, could anyone help me get my grub working again?

---

### Post by billgoldberg on 2009-01-26
Hmm, grub can be in pain in the back if something goes wrong.

I can suggest you take a look at the Super Grub Disk Live cd and see if you can boot into your Linux partition with that.

--

Another thing to do that would be easier is just reinstall Ubuntu, it will install the grub bootloader and configure it by default for a dual boot enviroment.

I say this because I presume you haven't been able to boot into Ubuntu.

Maybe something went wrong during installation.

---

### Post by deathscith on 2009-01-26
no, havent been able to boot into my ubuntu, ive tried re installing it a number of times, which just resulted in many many partitions laying around... i cleared most of them up, and am curious as to how i would go about installing a new grub, im fairly knew to linux...

---

### Post by deathscith on 2009-01-26
alright, just reinstalled it on the complete harddrive, so no more messing around with partitions, and now im getting an error 17... TO GOOGLE!

---

### Post by caljohnsmith on 2009-01-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

