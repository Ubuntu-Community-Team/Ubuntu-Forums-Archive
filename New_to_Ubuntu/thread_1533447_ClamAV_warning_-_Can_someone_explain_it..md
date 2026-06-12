---
title: "ClamAV warning - Can someone explain it."
date: 2010-07-18
forum: New to Ubuntu
---

### Post by itsols on 2010-07-18
I decided to run clamAV from the terminal. I came back after a while and found my screen flooded with lines similar to this one:

LibClamAV Warning: fmap_readpage: pread fail: asked for 4094 bytes @ offset 2, got 0

I don't know if the scan is still running as I only see the hard disk light blinking at irregular intervals.

Does anyone know what this means?

And if it means anything, I do have a Windows partition that I don't use anymore (except on a very rare occasion).

Thank you all for any advice.

---

### Post by potat on 2010-07-18
Above any of the lines does it say "Scanning <some file path>"? Clamscan might be scanning somewhere it's not supposed to, like /sys/ or /proc/.

---

### Post by potat on 2010-07-18
Just so you know, ClamAV usually isn't necessary unless you are running a big email server (checking for email viruses) or you are checking the Windows partition for viruses. Linux **doesn't get viruses.** :)

See [http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed](http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed)

---

### Post by itsols on 2010-07-18
Thank you for your feedback.

Please tell me if my exercise makes sense. Here are the details:

1. I run "sudo clamscan -r --bell -i /" hoping to do a full system scan. So are there still locations that it can't read?

2. A while back I visited a website. It surely seemed like a virus taking course. The site was not normal. Then I got some alert that the site's content could harm my computer. This is why I ran the clamav program.

---

### Post by potat on 2010-07-18
try the options
```

sudo clamscan -ir --exclude-dir=^/sys --exclude-dir=^/dev --exclude-dir=^/proc

```

It *can* read these directories, but they contain "files" that aren't really data or executables. Everything in /dev/ represents a piece of hardware. /proc/ contains files that represent running processes. /sys/ contains real-time system info/settings. So when Clamscan tries to scan these it probably gets confused.

Did you download any file from the website? In Ubuntu you are safe unless you execute the code yourself. A ".deb" installer can potentially contain malicious code but you would have to consciously download it from that site through the browser.
Firefox and Chrome will often give warnings about websites harming your computer. The warnings occur regardless of your operating system, so whatever that site had was probably Windows malware.

---

### Post by gseward on 2010-07-18
You said 
"A while back I visited a website. It surely seemed like a virus taking course. The site was not normal. Then I got some alert that the site's content could harm my computer."

What you ran into was a web site that was invaded by a malicious program/script, one that does this is Antivirus 2000, but there are others. It puts up a fake Antivirus warning saying you are infected, note that this is a web page you are viewing, not a legitamite AV product warning. Remember anything you see on a web page is coming from outside, not from your computer.
If you are in Linux you can thumb your nose at it and don't worry, it can't do anything to you. That is the long and short of it, no worry.
If you are in winblows get out of the browser right away [task manager], and DO NOT click on anything on the page, DO NOT allow a scan by this malware, and DO NOT BUY IT!  It will infect you with much malware.  You are not infected with anything unless you let it in by your actions.

---

### Post by itsols on 2010-07-18
Wow gseward!!! You said it just like you saw it :)

Actually the URL itself was one that belonged to my brother but the site was apparently 'hacked', so to say. I have no clue of how it happened but I brought it down and I have moved the site (using different source files) to a new server.

You are right that what I saw was a program running outside of my system. And yes, I am on Ubuntu. Windows sits in my laptop only because it came with the box. And of course for a rainy day - lol...

Thank you both for your tips so far. I'm yet to run a full scan using ClamAV... I shall post any updates after the scan.

Cheers!

---

