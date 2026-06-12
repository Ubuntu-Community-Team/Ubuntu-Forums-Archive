---
title: "Any FTP Client That Allows Me to Save Login Password?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by margazhang on 2008-12-16
I manage numerous websites and I need to FTP these websites often. gFTP and many others out there do not allow me to save the login passwords.

Is there any FTP client for Ubuntu that gives me the option to save passwords?

---

### Post by aysiu on 2008-12-16
FileZilla and FireFTP will.

---

### Post by oldos2er on 2008-12-16
I believe Nautilus will too.

---

### Post by Big_astur on 2008-12-16
Filezilla here and no problem. I manage many FTP as well.

I started using it on windows and of course since i changed to ubuntu. It is/was the faster FTP program on both OS of the ones i used.

---

### Post by skirkpatrick on 2008-12-16
I've been using the FireFTP addon to Firefox for a while now and am very happy with it.

---

### Post by morningboat on 2008-12-16
If you want to save the password in the encrypted mode, you also can try CrossFTP.

---

### Post by margazhang on 2009-01-01
> **morningboat said:**
> If you want to save the password in the encrypted mode, you also can try CrossFTP.

I tried downloading CrossFTP but looks like it needs java to be able to run it. Could someone give more detailed instructions as to how to make it run in Ubuntu?

I tried all other clients you guys recommended. FireFTP is the easiest one to use but is a bit slow compared to all others. FileZilla is fast but I have to highlight and drag files/folders to make transfer - it lacks the handy one-button upload/download function. Nautilus is fast too but it does not show local files/folders - I have to open another window for that purpose. Indeed all three can remember pwd which is nice.

I am still interested in CrossFTP as it has the ability to save pwd in encrypted form which is more secure. So any help with CrossFTP is appreciated.

Thanks all those who replied. God bless!

---

### Post by margazhang on 2009-01-02
OK, I figured out myself how to get the java environment in Ubuntu...

Basically, I clicked Applications -> Add/Remove and then I just searched for "java" to get "Sun Java 6 Runtime" the first on the list. I just marked it for install and rebooted the computer. Then I just typed the following command in the command line terminal:

```
javaws http://www.crossftp.com/crossftp.jnlp
```

It then downloaded and installed CrossFTP automatically. It runs pretty well.

There are some problems. The main one is that when I click the folder icon to open up the folder, it is very sluggish. This is true for Site Manager in choosing local path by browsing folders - I could only open folders down to the Documents folder and folders further down cannot be opened at all. 

Another thing... I see it allows me to set a Master Password to lock the use of the application but when I click the "Lock" button it does give a place for me to enter the Master Password. So I have to close the popup window - this locks me outside completely!

Hmmm... now I have to figure out how to force close the application :(

**Update:** could not close the application by running xkill - had to reboot and then when I run CrossFTP again it did allow me to enter the Master pwd. So do not lock the application right after you set the Master pwd. Lock means lock - just shut down the application and it can only be run again by entering a correct Master pwd.

The problem of not easy to open up a folder (whether local or remote) is still not resolved - have to ask the author about this problem.

---

### Post by crossftp on 2009-01-06
> The problem of not easy to open up a folder (whether local or remote) is still not resolved - have to ask the author about this problem.
The folder open function uses a standard Java file open dialog, hence it should work fine. This problem is not met before. You'd better to have 100M+ free memory space to allow the program to run in full speed. If you have problem in opening a file dialog to set up the local path, you can fill in the local path's text box as well instead of opening up a dialog.

---

### Post by aev on 2009-02-13
> **margazhang said:**
> I manage numerous websites and I need to FTP these websites often. gFTP and many others out there do not allow me to save the login passwords.

Is there any FTP client for Ubuntu that gives me the option to save passwords?

gFTP allows you to save passwords. As a bookmark for example. That's how I have set it up to log from laptop to my desktop.

---

### Post by margazhang on 2009-04-25
Just an update as to which one I settle down with. FileZilla is the winner! 

After upgrading Ubuntu to Jaunty 9.04, the link to FileZilla was missing, but after following [instructions posted here]("http://ubuntuforums.org/showpost.php?p=7148216&postcount=6"), it is working again!

---

