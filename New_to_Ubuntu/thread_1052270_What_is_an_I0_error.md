---
title: "What is an I/0 error?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by HarmonicaGoldfish on 2009-01-27
Tried to do a fresh install of 8.10 due to a few issues I've developed as a result of some strange updates (I think) ([see here]("http://ubuntuforums.org/showthread.php?t=1049275")).

I downloaded the ubuntu 8.10 desktop i386 iso from the ubuntu website. I checked the md5sum on completion of the download and it matched the official sum. I wrote the file to a disk then restarted my system. I got through to the main menu, chose install, and after the ubuntu splash screen hung out for a while got these 2 messages over and over again:

Buffer I/O error on device sr0, logical block 178898
end_request: I/0 error, dev sr0, sector 1431184

So I tried again and still no go.

Do you know what this means?
thanks
Tracy

---

### Post by kestrel1 on 2009-01-27
Sounds like the disk hasn#t burnt correctly.

---

### Post by Therion on 2009-01-27
Re-burn the CD/DVD and burn it slooooow.  No more than half the speed the media is rated for.

---

### Post by HarmonicaGoldfish on 2009-01-27
Thanks - I did exactly that and it worked like a charm. I'm so glad I did this fresh install...so far! At least my network manager works now.

Is it normal to have 226 updates with a fresh install?

---

### Post by kestrel1 on 2009-01-27
Yes 226 or more is normal for a fresh install of 8.10.

---

### Post by Anthony King on 2009-03-18
I was having the same problem as the OP, the strange thing is that I used the same disc yesterday to install Ubuntu on another computer without any problems.  I also used the check disc utility without turning up anything.

I was receiving the same message described by the OP, but because of the reasons above I felt the disc might be fine and continued to let the disc run on a hunch, and while I did receive some other logical error messages (357977) the disc did--with much labor--boot.

---

### Post by skymera on 2009-03-18
I get I/O Errors when i have a USB device plugged in.

Try unplugging iPods, or flash drives etc

---

### Post by arapa on 2009-03-18
I don't know if it's my imagination but when I burn the ISO as 'disk at once' rather than my burning software's default (and slower as indicated above) it seems to eliminate the I/O problems.

---

