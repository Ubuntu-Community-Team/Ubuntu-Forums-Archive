---
title: "dual boot security windows offline"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Bear number one on 2009-11-01
I am planning to dual boot my computer with ubuntu and vista only allowing the ubuntu installation to have access to the internet.  Vista will be used offline. I understand that antivirus etc is not necessary in a linux installation but will it still be necessary to use antivirus or a firewall on the vista partition?
I have read a previous thread which, if I understood it correctly, said that a virus could not jump partitions, is this correct?

---

### Post by gn2 on 2009-11-01
You can write a virus to your Vista partition while booted into Ubuntu.

Edit: an example would be using Ubuntu to download a driver for Windows, it would be perfectly possible to download an infected file, unless you chose to scan it you wouldn't know for sure what it contained.

---

### Post by Bear number one on 2009-11-01
> **gn2 said:**
> You can write a virus to your Vista partition while booted into Ubuntu.

Edit: an example would be using Ubuntu to download a driver for Windows, it would be perfectly possible to download an infected file, unless you chose to scan it you wouldn't know for sure what it contained.
I have bit defender for unices installed on ubuntu so I can scan a download, not sure how effective it is though.  But if I was to use vista solely offline without adding any downloaded software would it be possible for, say, a drive by virus to download to the ubuntu partition and jump from the ubuntu partition to the vista partition. Sounds a bit crazy but I'm a bit confused about this.

---

### Post by seshomaru samma on 2009-11-01
It seems highly unlikely that you would be able to infect a Vista partition from Ubuntu unless you are trying really hard. 
In theory you could download something and put it in a shared partition and then when you switch to vista run that file, but it seems unlikely....

---

### Post by Citadel1980 on 2009-11-01
I agree to what Seshomaru Samma stated. It is highly unlikely. The problems occur mainly when you are sharing files between Windows and Linux or if you download something in Linux and then share that file with a Windows computer or another Windows user.

Many people use an anti-virus program in Linux to scan any files that will be shared with Windows.

---

### Post by Bear number one on 2009-11-01
So an offline windows partition could only get infected by an unscanned infected file shared on to it's own partition?
A virus couldn't download from the online linux system and 'jump' the linux partition to get onto the windows partition?
Or maybe in theory but not likely in general use. I think I'm starting to understand.
No need for a firewall on the windows partition either because of the nature of ntfs vs ext4?
I take it that when one partition is booted up the other is dormant?

---

### Post by Xero Xenith on 2009-11-01
For Windows to get infected, it needs to have a virus on it, of course. Viruses are transmitted in files; any way you can get a file onto Windows is a potential way to transmit a virus. So it's not limited to just its own partition - USB drives, CD-Rs, DVD-Rs, etc could also hold viruses, but of course, someone would have had to put it there, and you'd have to open the infected file yourself, before the virus can do anything.

For a file to get there via Linux, either Linux would have to put it there (pretty much impossible) or Windows would have to read it from the Linux partition (impossible unless you install some special software so Windows can read from Linux partitions, e.g. ext3, ext4, etc).

So it's very unlikely that Windows could get a virus without the Internet, but remember to be very wary about what you connect, like USB keys or CD-Rs. And because you can never be sure, I'd recommend at least a basic virus scanner, like AVG Free.

---

### Post by Mark Phelps on 2009-11-01
> **Bear number one said:**
> I have read a previous thread which, if I understood it correctly, said that a virus could not jump partitions, is this correct?

Not true -- a virus can easily "jump partitions".

What it's not going to do is jump OSs.

But if you have Vista and Ubuntu on the same machine, any file you download from the internet (if not scanned) has the potential of containing a hidden virus.  If later, you open or run that file from Vista, and the file is infected, then Vista becomes infected.

---

### Post by ranch hand on 2009-11-01
ClamAV is installed by default in your Ubuntu if you are using 9.04 or 9.10.

I wouldn't worry too much.  I would scan anything you do not get from MS.

Keep in mind that I will not have MS on my machine so I may be a little apathetic to infection in Win JerryLewis Pro.

---

### Post by Bear number one on 2009-11-02
[quote=Mark Phelps;8218189]Not true -- a virus can easily "jump partitions".

What it's not going to do is jump OSs.

Many thanks to all who have answered, the quote above has cleared up most of what I was puzzled about! In general it seems that as long as I scan any ms files downloaded via Ubuntu before opening them in Vista I should be o.k. As mentioned before I have Bitdefender for Unices installed on Ubuntu.  I may take a look at portable antivirus scanners as well.  Interesting that a virus can 'jump' partitions depending on the os.  I will take a further look into this also.  Thanks again to all for pointing me in the right direction.

---

