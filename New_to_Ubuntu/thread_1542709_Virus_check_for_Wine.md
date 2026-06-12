---
title: "Virus check for Wine"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-07-31
If I download a .exe file, should I check it before I run it on Wine?
    How do I do that? I have clamav installed on my system. Is that enough to check for a  Windows virus?

Another thing - If clamav does not catch a Windows virus, is it really necessary to have it? I mean, there doesn't seem to be any way to get a virus on my Linux installation unless I search out a virus and run it on purpose.

---

### Post by marshmallow1304 on 2010-07-31
ClamAV does search for Windows viruses - that's its purpose, but I believe it needs to be started manually (something like 'clamscan -r ~/.wine').  For a single or a few suspicious file(s), I recommend [Jotti's malware scan]("http://virusscan.jotti.org/"), a free online tool that scans uploaded files with many different scanners.

---

### Post by Paqman on 2010-07-31
ClamAV isn't particularly effective, i'd recommend using something like Avast if you're trying to spot Windows viruses.

---

### Post by beew on 2010-07-31
clamav is crap. Get a real av like avast or bitdefender :)

clamav is an inferior product, peroid. I don't care if it is FOSS.

---

### Post by ankspo71 on 2010-07-31
Hi,
It's up to you whether scanning for windows viruses in windows executables is necessary, or files in your wine directory is necessary, but I would recommend doing it if you don't trust the files or the sources where they came from.

For a basic scan, clam should be enough, but I would look into different software (or more software) if you need higher virus detection rates. There is a surprisingly large number of Antivirus software that runs in Linux, see: [http://en.wikipedia.org/wiki/List_of_antivirus_software](http://en.wikipedia.org/wiki/List_of_antivirus_software)

Here is a recent article for antivirus in Linux. 
[http://www.tuxradar.com/content/get-best-virus-scanner-linux](http://www.tuxradar.com/content/get-best-virus-scanner-linux)
(they feel bitdefender wins)

---

### Post by Lucifer The Dark on 2010-07-31
I don't know if I agree about ClamAV being inferior, I've had it find more than one virus that Avast in Windows missed.

---

### Post by Paqman on 2010-07-31
> **Lucifer The Dark said:**
> I don't know if I agree about ClamAV being inferior, I've had it find more than one virus that Avast in Windows missed.

[http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness](http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness)

No one AV product finds everything, but ClamAV is not a very good performer.

---

### Post by Fifthmarch on 2010-08-10
Have installed BitDefender in my system - Scan shows no viruses. Thanks!

---

### Post by inameiname on 2010-08-10
It's always quite the back and forth thing in regards to whether or not Clamav works well or not. I've heard it both ways from one extreme to another. It's always so hard to actually take a side. Hehe. Guess it's all about personal preference. For me, I've never had issues with it. To each their own, I guess.

---

