---
title: "I Used To Not Have An Internet Connection Problem..."
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Jobiwan on 2007-05-19
Hello Ubuntu Forum Friends,

Normally I scour the internet to solve ALL problems, 
but I'm stumped on this one.

Up until now, I have been using the Networking application 
to access the internet, along with a Best Data external modem, 
which has served me well.

My problem started when I decided to add several more
phone numbers to the line using only commas. I found out 
later that I should have used colons instead. No matter what
I do, I can't make that string of numbers go away, and the
application won't let me dial out.

[B]My best guess is I believe I need to go to the file and alter it,
removing that string of numbers, but I have no idea where to look.[/B]

I've also tried gnome-ppp, kppp, wvdial, and pppconfig according
to these instructions: 

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

All to no avail. I'll have to go back and try them again to make sure,
but I believe only wvdial lets me connect and stay connected, but I
can't open any browsers (Firefox/Konquerer), and also tried the Update
Manager while connected, but can't get anything. My modem says I'm
connected and I can hear the squeal from the phone line, but that's it.

I don't mind which app I use, so long as I can dial out.

I've dabbled a little with SUSE 9.2 and Debian 3.1, and I have to say
that Ubuntu is the distro that can really wean me off of Windows for good.

Keep it up Ubuntu Friends!!!

Joe

---

### Post by Jobiwan on 2007-05-23
Hey Guys and Gals,

I got my internal winmodem up and running, but not
my external modem. Here's what I did.

Luckily, I'm dual-booted with Windows and the hard disk icon 
is on my Ubuntu desktop. Every time I needed to download 
anything for this project, I would shut down, go to Windows, 
put the downloaded files that I got with my external modem, 
in a Temp folder. 

These files included the modem driver, scanModem, and the 
three linux-headers. I got the build-essential from the Ubuntu CD.  

After I placed everything I needed in that Windows folder,
I would go back to my Ubuntu desktop and retrieve them.

Then I looked closely at the information in the ModemData.txt 
file and the brief instructions from a link that was included from 
one Ubuntu Forum thread ( [http://ubuntuforums.org/showthread.php?t=185079](http://ubuntuforums.org/showthread.php?t=185079) ) 
Then after a lot of head-scratching and chin-rubbing, I'm connected 
with wvdial, KPPP, and gnome-ppp so far. I'm still not able to use 
my external modem, though. I'll figure that one out after I take a little break.

By the way, the files that are in the ScanModem folder are useful.
Just take your time, read, organize your steps, and BE PATIENT.

Chow Man,
Jobiwan

P.S. After I took a little break, and a deep breath, I got back on the 
net, and now I have two HDDs installed on my main computer. One 
has Win2K Pro (slave), the other has Ubuntu/Win ME (master). DANG! 
This is fun! (Now, where did I put that hard drive with WinXP Home/SUSE 9.2
on it at?)

P.P.S. Regarding the Win2K Pro hdd, it was down for about week with
a blue screen that said, "INACCESSIBLE BOOT DEVICE", wouldn't even
get to the desktop. I said (Yeah, I talk to myself. I'm the best friend I've got!),
"Well, great! Now it's a virus or the hard drive is going out!" After searching
far and wide around the globe (I've got Indiana Jobiwan in me), I came across
THIS... [http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)  a  hdd manufacturer's
list of diagnostic tools and utilities. Seagate's SeaTools fixed my problem (I
have a Maxtor hdd, which they bought out). The thing I noticed was that some
hdd manufacturer's have utilities that diagnose and FIX the problem, and some 
only tell you what's wrong (I won't buy another Samsung hdd). Well, I'm done.
Time for another beer! Ya'll have a GREAT weekend!

---

