---
title: "Accessing Thunderbird Profile Remotely on Windows Server from Ubuntu"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by mikeypc2006 on 2009-07-23
This might sound strange, but bear with!  I have a desktop computer which I use as a server running Windows 98.  (As a side note, this will one day become a different desktop running Ubuntu Server or something, but the current computer isn't powerful enough to cope with the Ubuntu Server spec).  On this computer, I have my Thunderbird profile.  I currently access this from Thunderbird on a separate desktop running Windows 7 RC.  I want to be able to access the same Thunderbird profile from my Ubuntu laptop.  Could I copy my profile.ini file from Windows to Ubuntu without modifying it to access the same network path or does Ubuntu see network pathes differently than Windows?

What I want to know is, how do I go about accessing my Thunderbird profile on my Windows server from Thunderbird on my Ubuntu laptop?

I found this old thread on a fairly similar topic [http://ubuntuforums.org/archive/index.php/t-691894.html](http://ubuntuforums.org/archive/index.php/t-691894.html)  I'm willing to take the risks and would only consider IMAP as a very last resort, I would much rather look after my own email without trusting it all to someone else, though there are benefits too.

---

### Post by llamabr on 2009-07-23
I was going to suggest IMAP, but don't understand your reservations.  With IMAP, the mail will stay on the server, but will be available on your laptop.  Who's the middle man you're worried about?

---

### Post by oldfred on 2009-07-23
I use a common FAT32 directory for thunderbird. The ini files are not the same as the paths are different. If you mount your network directory where the thunderbird files are in Ubuntu with the proper read/write settings and edit the Ubuntu file in .mozilla-thunderbird it will work.
My windows path: 
Path=H:\mozilla\thunderbird\profiles\lyu25irb.default
My Ubuntu path:
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
where I mounted the same partition as H: is in windows as /home/fred/share

---

### Post by mikeypc2006 on 2009-07-24
> **llamabr said:**
> I was going to suggest IMAP, but don't understand your reservations.  With IMAP, the mail will stay on the server, but will be available on your laptop.  Who's the middle man you're worried about?
I would still need to backup the IMAP server to ensure that if the IMAP server were to go down for whatever reason, I don't loose all my email.
> **oldfred said:**
> I use a common FAT32 directory for thunderbird. The ini files are not the same as the paths are different. If you mount your network directory where the thunderbird files are in Ubuntu with the proper read/write settings and edit the Ubuntu file in .mozilla-thunderbird it will work.
My windows path: 
Path=H:\mozilla\thunderbird\profiles\lyu25irb.default
My Ubuntu path:
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
where I mounted the same partition as H: is in windows as /home/fred/share
That's cool, thanks, I will give that a try :)

---

### Post by mikeypc2006 on 2009-07-24
Sorry for the double post.

I captured the network path to my server for my Thunderbird profile from my Ubuntu laptop.  I edited the profile.ini file with the network path and changed 'is path relative' to 0.  However, when I try and run Thunderbird, it just creates a new Thunderbird profile in my home directory on my laptop.  How do I tell Thunderbird to connect to my profile on my server?

This is what my profile.ini file looks like: -

[quote=code]
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=smb://michael-server/my%20documents/eMail/Thunderbird/Profiles/g25uwo91.default
[/quote]

---

### Post by oldfred on 2009-07-24
I have a default = 1 as the last line in both windows & ubuntu? And with FAT I did not have to worry about permissions, are yours set correctly?

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

---

### Post by mikeypc2006 on 2009-07-29
The Thunderbird profile is accessible from Windows from the server with full read/write permissions set, so presumably that isn't the problem for Linux?  I added 'default=1' to the 'profile.ini' file in Ubuntu and yet it still created a new profile folder and completely ignored the network.  The network folder on the server is mounted, though I have to mount it manually by going to 'Places', 'Network' etc.

Any ideas, this is getting irritating!

---

### Post by oldfred on 2009-07-29
I overwrote the profile.ini that thunderbird created the first time I started it in ubuntu and it found the shared files. If the shared file directory is renamed it says it is already running but does not create a new profile. I think you can permanently mount a windows share in fstab wwith something like this as the last line in you /etc/fstab:
[COLOR=#ff0000]//*servername*/*sharename* /*mountdirectory* smbfs username=*windowsuserename*,password=*windowspassword* 0 0
[COLOR=black]
Then check that you can write to that directory.[/COLOR]
[/COLOR]

---

