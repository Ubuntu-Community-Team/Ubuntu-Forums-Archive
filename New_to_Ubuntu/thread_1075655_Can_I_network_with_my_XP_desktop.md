---
title: "Can I network with my XP desktop?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by sailthesea on 2009-02-20
I was wondering if it is possible to use my wireless laptop with 8.10 to network with my XP desktop in order to access my library and print stuff etc? I,m new to both wireless and Ubuntu so don't really know where to start
 The alternative seems to involve lots of discs and running up and down the stairs!
 Any tips on where to begin?

Thanks

---

### Post by HermanAB on 2009-02-20
In order from very easy to very difficult:
1. FTP (Install Filezilla server on Windows)
2. FTP (Install proftpd on Linux and Filezilla client on Windows)
3. NFS (Install Services for Unix on Windows (Free download from MS) and NFS server and client on Linux)
4. SMB (Share a file folder on Windows and install Samba client on Linux)
5. SMB (Install Samba server on Linux)

Cheers,

Herman

---

### Post by sailthesea on 2009-02-20
OK 
 I looked at No 1 and even that seems a bit beyond me at the moment I shall have to read up a bit more on inter platform networking. I did try to add this machine to the network from windows with a view to uploading the files I need to Ubuntu Directory, but it dual boots win 2000 which is hardly up the the job. For now I'll have to put what I need on a cd  and come back to this problem when I am more confident. At least I know what I want to do is possible so thanks anyway.
 If there is anywhere you know of to start a bit of VERY basic reading that would be great!
 Thanks again

---

### Post by rgb96 on 2009-02-20
FTP is pretty easy. Windows XP comes with an FTP server service preinstalled, you just have to start it. After you set it up, you just access with with your web broswer from the other computer. That will alllow you to transfer files from comp to comp easily.

Here is a tutorial that can help get you started: [http://www.pcstats.com/articleview.cfm?articleID=1491](http://www.pcstats.com/articleview.cfm?articleID=1491)

---

### Post by spcwingo on 2009-02-20
Yes.

```
sudo apt-get install samba smbfs
```

---

### Post by Kellemora on 2009-02-20
Hi SPC

I hate to bump heads here, but about the only thing smbfs will do is PREVENT several of the shares from appearing!

Want proof?

Install smbtree then check the number of shares that appear when you run smbtree in terminal.

Now, install smbfs and check them again using smbtree.
I think you will find a few missing!

Now, unistall smbfs and check again, and voila, the shares are back!

It took me nearly a month to figure out why some shares were not showing and others were.  And discovered it totally by accident.  One machine always showed ALL our shares, never gave us a problem, until I noticed when looking through Synaptic that smbfs was not installed on that machine.  I installed it and bam 1/3 of the shares disappeared.  And I knew that was the one and only change I had made to that computer.  
I went to all of our machines and removed smbfs and then all the shares showed up on all of them thereafter.  Except of course for the BUG in Nautilus which appears from time to time.  But that's a whole different story.

TTUL
Gary

---

### Post by spcwingo on 2009-02-20
> **Kellemora said:**
> Hi SPC

I hate to bump heads here, but about the only thing smbfs will do is PREVENT several of the shares from appearing!

Want proof?

Install smbtree then check the number of shares that appear when you run smbtree in terminal.

Now, install smbfs and check them again using smbtree.
I think you will find a few missing!

Now, unistall smbfs and check again, and voila, the shares are back!

It took me nearly a month to figure out why some shares were not showing and others were.  And discovered it totally by accident.  One machine always showed ALL our shares, never gave us a problem, until I noticed when looking through Synaptic that smbfs was not installed on that machine.  I installed it and bam 1/3 of the shares disappeared.  And I knew that was the one and only change I had made to that computer.  
I went to all of our machines and removed smbfs and then all the shares showed up on all of them thereafter.  Except of course for the BUG in Nautilus which appears from time to time.  But that's a whole different story.

TTUL
Gary

I've never had that problem.  Maybe I'm just lucky.  :)

---

### Post by sailthesea on 2009-02-20
Um in the meantime..
  I've been checking out FTP and it looks like the way to go with what I'm using. Thanks rgb96, I will have to get to my desktop machine first, one of the main reasons for dusting off this ancient laptop and trying Ubuntu is because I never get use the home computers, at least no one will hijack this one!
  Cheers

---

