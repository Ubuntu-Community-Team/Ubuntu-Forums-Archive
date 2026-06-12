---
title: "HowTo: Download MP3 albums from Amazon"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Trent T on 2011-04-21
Downloading MP3 music from Amazon - There are a few tricks to it!  These are the steps I wish I had followed this morning;

Pre-requisites:
You need an Amazon account, and the Amazon MP3 Downloader.

1) Log in to your Amazon Account
2) Search MP3 Downloads.  This will get you to the MP3 download section.
   Amazon has a 'Free MP3 download of the day.'  
   Download it even if you don't want it. This will let you get your system
   set up to download stuff that you DO want.
3) Click on the free Download file.
4) Click [Get MP3] button.
   At some point, Amazon will prompt you to download the Amazon MP3 Downloader.  One of the 4 options is a Downloader for Debian or Ubuntu 9.04.
5) Install this on your system.  It will eventually end up in your Applications menu under Internet.
   Open the Amazon MP3 downloader, and specify the directory where you want your MP3's to live-- Usually /Music/AmazonMP3...

6) Exit Amazon.
   "What about my free song?" you ask?  Well, you didn't want it anyway,
   and it was mostly there to get you to the 'downloader'.

Downloading Music:
7) Start Amazon MP3 Downloader, and click the 'Shop Amazon MP3 Store' button in the upper left.  This will take you directly into Amazon, logged into your account.

8) Find and click on the free download MP3 that you didn't want.

NOTE:
   If Amazon asks you again to download the Amazon MP3 Downloader, look carefully at the fine print underneath the 4 Download buttons-- You will find a clickable message that says, 
"Already downloaded the Downloader? Click [HERE] to synch it with your Web browser.

9) Receive informative error message;
   Error: Unable to save /tmp/AmazonMP312345679810.amz
   Try opening the file and then saving it.
 
   ** This means that the Amazon file that will become your MP3 
   has been parked in your /tmp directory.

10) Open the Amazon MP3 downloader.
    Click File, then 'Open AMZ file'
    Type /tmp/  ...
    and as you type, you will see the Amazon .AMZ file in the list of 
    TMP file flotsam.
    Click on the file, and the Amazon MP3 downloader will finish downloading your file, and park it in the default directory you specified for Amazon MP3's.

11) NOW, you can try downloading music that you really want!

Other information;
The Amazon help desk is shaky on Linux.  My help rep told me that they don't support Linux, or at least not 64-bit.  It worked for me, and I convinced him too, after a while...

I am running Ubuntu 9.10 on a 32-bit system.

---

### Post by oldos2er on 2011-04-21
For 64-bit Ubuntu, there is [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/) and [http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)

---

### Post by mobilediesel on 2011-04-21
Downloading MP3s definitely wasn't as straight forward as it should be on Amazon. I did discover, recently, that Opera 11.10 is able to download from Amazon without their software installed. My system is 32 bit so I can't say whether that works with 64 bit.

---

### Post by rosencrantz on 2011-04-21
Note for recent Ubuntu (e.g. Maverick): There are unsatisfiable dependencies (old boost libraries). This helps
[http://linuxnoise.wordpress.com/2010/10/09/installing-amazon-mp3-downloader-on-ubuntu-maverick-10-10/](http://linuxnoise.wordpress.com/2010/10/09/installing-amazon-mp3-downloader-on-ubuntu-maverick-10-10/)
Also, Banshee apparently has an Amazon download plugin. Amarok hasn't :-(
Edit: +1 for pymazon, btw. There's no need for that silly Amazon app and installing dated libraries.

---

