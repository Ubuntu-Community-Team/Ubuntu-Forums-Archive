---
title: "Teamviewer 6 - Package Operation Failed"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by DubDubZA on 2011-06-27
Hi Guys,

I only started using Ubuntu a few days ago (i.e. as green and fresh as you will ever get - so please be patient).

I am having difficulty installing Teamviewer 6 using the Ubuntu Software Center. I keep on getting a "Package operation failed" message.

```
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 135338 files and directories currently installed.) 
Unpacking teamviewer6 (from /tmp/teamviewer_linux-2.deb) ... 
dpkg: error processing /tmp/teamviewer_linux-2.deb (--install): 
 corrupted filesystem tarfile - corrupted package archive 
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe 
Processing triggers for menu ... 
Errors were encountered while processing: 
 /tmp/teamviewer_linux-2.deb
```I am currently running Teamviewer , using the tar.gz file using Wine. But would really like to do a native install for this software.

Can anyone please help (preferably step-by-step instructions if possible as Ubuntu is still very foreign territory to me).

Thanks in advance.

---

### Post by scheuri on 2011-06-27
If you read the error messages again, you will pretty much see where the problem is/likely might be:

```

dpkg: error processing /tmp/teamviewer_linux-2.deb (--install): 
 corrupted filesystem tarfile - corrupted package archive 
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe 
Processing triggers for menu ... 

```

If that is correct what is says, then something might have gone wrong downloading it.
Please remove that .deb-file and re-download it from the official website.

---

### Post by candtalan on 2011-06-27
I use teamviewer ok.
Download from (linux)
[www.teamviewer.com/en/download/index.aspx](www.teamviewer.com/en/download/index.aspx)
[www.teamviewer.com/download/teamviewer_linux.deb](www.teamviewer.com/download/teamviewer_linux.deb)
(I use 32 bit)
Save the file onto your PC.
Right click onto the saved file and choose open with gdebi package installer.

Continue with the installation and allow it to complete.

After installation I find it in the (applications) (Internet) list.
hth

---

### Post by DubDubZA on 2011-06-27
Thanks guys it does appear that there is something wrong with this file.

I have downloaded it more than once and from different machines. I have also tried installing the files with Ubuntu Software Center, and GDebi Package installer.

I will send a message to the Teamviewer support team to have a look at this.

If anyone could check that my assumption is correct, by downloading and instaling the 32bit deb package it would be appreciated.

Thanks for all the quick replies.

---

### Post by candtalan on 2011-06-28
> **DubDubZA said:**
> Thanks guys it does appear that there is something wrong with this file.

I have downloaded it more than once and from different machines. I have also tried installing the files with Ubuntu Software Center, and GDebi Package installer.

I will send a message to the Teamviewer support team to have a look at this.

If anyone could check that my assumption is correct, by downloading and instaling the 32bit deb package it would be appreciated.

Thanks for all the quick replies.
I downloaded the 32 bit deb file again just now from
[www.teamviewer.com/download/teamviewer_linux.deb](www.teamviewer.com/download/teamviewer_linux.deb)
and compared it with the original file I downloaded some weeks ago and originally installed using the Ubuntu 10.04.2 gdebi package manager (the teamviewer6 I am currently using).

I did an md5sum on the new downloaded (today) file and also on the original old file and the md5sum value is the same for each. So I conclude that I think the file offered there for download is good and works ok, in my ubuntu 10.04.2

You might like to look at the file you have downloaded yourself and do an md5sum on it, to see if it is the same. Later builds may be different but just now this is what I am finding.

For your information md5sum of the (current and the older one)
teamviewer_linux.deb
 I find is
968f9c674ec2a6dca63682f7433bc59b

---

