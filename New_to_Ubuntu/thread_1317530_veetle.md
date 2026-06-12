---
title: "veetle"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by genetik on 2009-11-06
I downloaded the .sh from the veetle site and ran it in the terminal.  No errors occurred.  But when I find a stream it says that veetle is not installed.  I'm using the 64-bit of 9.10 - are there any known conflicts with my version of firefox or flash perhaps?

---

### Post by happyisland on 2009-11-18
I'm having the same issue -- anyone out there know why this is?

---

### Post by hardev on 2010-01-06
Same here. Seems to be a Firefox 3.5.x issue. Can anyone confirm it?

Veetle Download page:
[http://www.veetle.com/download.php](http://www.veetle.com/download.php)

---

### Post by hardev on 2010-01-06
I'm running Ubuntu Karmic 32-bit. I have tried installing Veetle via "sh" script and tarbell. No luck so far.

---

### Post by genetik on 2010-01-08
I haven't figured it out either.

---

### Post by verlyn13 on 2010-01-16
Same problem.  Running 64-bit Ubuntu with 2.6.31-18-generic kernel and firefox 3.5.7.

---

### Post by PostWax on 2010-02-04
Smae here.  9.04 64 bit.  Thanks.

Ron

---

### Post by Yozhik on 2010-02-06
9.10 32 bit
Can't run Veetle 0.9.16
Tried both sh. and tgz.

Nothing
Nada
Nix

---

### Post by PGScooter on 2010-02-13
9.04 64-bit. no luck either .

---

### Post by angualupin on 2010-02-21
I had this same problem and seem to have solved it by installing VLC Player (through Synaptic Package Manager). Apparently Veetle uses VLC, which the Veetle site does not tell you.

I make no promises that this will solve everyone else's issues with Veetle, but it solved mine.

---

### Post by jahja on 2010-02-21
Hey guys - 

I was also having this problem. I just got it working, in 64bit 9.10 and the latest swiftfox.

I couldn't get it to work with the script, then I tried the .tgz file from veetle website.

There is an instructions file inside....followed it to the T and it is working beautifully!!

I don't know if it will work in normal firefox, but I would seriously suggest swiftfox anyway if you haven't tried it. It is swift indeed!!

Also been trying out different torrent clients...and Vuze seems to be the speed demon for me in 64bit 9.10.....in the previous version I'd found deluge to be best, but Vuze has been far better for me today....tested on several downloads.

---

### Post by greenjumper on 2010-04-06
Veetle know that there is a problem with the support for 64 bit versions of Linux and are trying to sort it out - although they have been for a while. 
Meanwhile I have managed to get it to work by installing the Flock web browser. It can be easily installed using the deb [here]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=flock")

In this browser it works normally as it should.

---

### Post by rolandrock on 2010-04-25
This solution applies to 64bit users who have tried to use the veetle-xxxxxx-linux-install.sh script with swiftfox and failed.

After reading jahja's mail, I compared the instructions in the tgz with what the installer does.

The installer copies one more file ( ~/.veetle_vlc/lbclient ) compared to the tgz instructions so I renamed ~/.veetle_vlc/lbclient to lbclient_bak and restarted swiftfox.  IT WORKED.

Note: this only works for swiftfox - firefox still can't play veetle.

Regards
RR

---

### Post by Don1500 on 2010-04-25
Ran the sh script in terminal, worked as advertised. Went to the Veetle site loaded video for a number of movies and live feeds, no problems.
Using Ubuntu 9.10, Firefox 3.5.9

Video is not that good, would like to see improvement there.

---

### Post by diamondnular on 2010-04-26
> **genetik said:**
> I downloaded the .sh from the veetle site and ran it in the terminal.  No errors occurred.  But when I find a stream it says that veetle is not installed.  I'm using the 64-bit of 9.10 - are there any known conflicts with my version of firefox or flash perhaps?

Simple. Veelte is 32bit application and you use 64 bit application (Firefox, Chrome) to run it. You can try Flock or Swiftfox (turn out to be 32 bit application) or try to install 32 bit application (for example Firefox 32, Chrome 32) on your 64 bit system. This solution should work! (and it worked for me).

---

### Post by lespedeza on 2010-08-21
> **diamondnular said:**
> Simple. Veelte is 32bit application and you use 64 bit application (Firefox, Chrome) to run it. You can try Flock or Swiftfox (turn out to be 32 bit application) or try to install 32 bit application (for example Firefox 32, Chrome 32) on your 64 bit system. This solution should work! (and it worked for me).

This also worked for me (running Ubuntu 9.10 - 64 bit), installed flock, made sure veetle plugin was in correct location and now have veetle working.  So far no issues.

---

### Post by htunnayshin on 2010-10-04
no it did not solve my problem, i do not know what to do anymore.

---

### Post by diamondnular on 2010-10-04
> **htunnayshin said:**
> no it did not solve my problem, i do not know what to do anymore.
What did you do?

---

