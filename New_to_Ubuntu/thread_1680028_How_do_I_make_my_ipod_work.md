---
title: "How do I make my ipod work?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by melinda on 2011-02-01
I just bought a used apple ipod nano 8gb and it was reset when I bought it.  when I put music on it with rhythm box it shows up on the device but when I eject it, nothing is there...do I need to re-format it so it works on Ubuntu? Please, anyone, I know this is a dumb question but if you know...tell me Come on please??? I know you guys get a lot of questions like this

---

### Post by DMKryl on 2011-02-01
Apple has close politics then it comes to their hardware and software, you (right now) can't put music in your ipod because it simply won't write in the ipod the songs (say thanks to apple), anyway right now your best shot is to try installing itunes and run it from wine, if it doesn't work try virtualization (if you don't know about it google it too large to explain) with an win xp, if all of that fail simply dual-boot to xp move your music in.

---

### Post by dirghrabadia on 2011-02-02
You might want to check out gtkpod ([http://www.gtkpod.org/wiki/Home](http://www.gtkpod.org/wiki/Home)).

---

### Post by taseedorf on 2011-02-02
you have to put your iPod into disc mode, so it acts like a usb device.  than you can add songs to it,  however, it wont sync the same.

---

### Post by panderohit on 2011-03-02
Hi melida. Don't worry you can do it. I did and my ipod works beautifully. This has been covered in another thread. My response has been copied as under. It will take a bit of work but it will work like native.

> [QUOTE]Download Virtualbox from their site (The open source one isn't as   featured as their closed source one, so get the closed source one)
 Install it
 Install Windows onto it
 Install an ipod manager in Windows
 Get your music onto the windows OS via USB or shared folders...
 mount the IPOD in Windows. 
I installed Windows 7 in a Virtualbox downloaded from their website.  Then I had to tinker a bit to enable the usb-connections. Once set, I  downloaded iTunes and synced my iPod from there and it works *perfectly*.

I tried using Rhythmbox and gtkpod but received limited success from  all. In the case of Rhythmbox, only the .mp3 files and the .mov files  would sync but none of the others.

The problem was the same with gtkpod. However most of my music and video  files were in .m4a and .mp4 format and none of these software would  recognise it. However through iTunes it worked beautifully. The only  hitch was that it was extremely slow. It took more than double the time  it normally takes on Windows Vista, but I am not complaining. It saves  me the trouble of dual booting and being unable to use Ubuntu while  managing my iPod.

However, it is necessary to have a Windows Installation Disk ready for  installing the OS in virtualbox. I was lucky as I got Windows 7  pre-installed in my laptop and received the disks alongwith it; however I  am aware that an installation disk can be created through windows. I  would recommend that you ask someone or google it to find out how. You  may need the dreaded Windows Registration Key. :sad:

I recommend giving it atleast 20 GB of your hard drive space. Also, I'd  recommend downloading an anti-virus into this virtual machine for your  protection and try not to use it for downloading anything other than  from the iTunes store if you wish to avoid the windows viruses from  playing havoc on your ubuntu machine.

All the best.[/QUOTE]

Wish you all the best. Trust me, it is worth the hassle. Once installed, it will work without a problem.

---

### Post by kkkkatie on 2011-05-19
really stupid question - how do you stick the ipod into disc mode? 
I got the 6g nano (touch screen) in 11.04 and banshee thinks it adds/deletes music etc but the ipod doesnt and when i re-connect the ipod the data is under 'other' rather than music. so frustrating!!!

---

