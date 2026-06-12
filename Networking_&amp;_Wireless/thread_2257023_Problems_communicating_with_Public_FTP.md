---
title: "Problems communicating with Public FTP"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by chris330 on 2014-12-16
Hello,

I am having issues connecting to a public FTP hosted on a Windows Server 2012 R2 machine. The device that's giving me problems is running Ubuntu 8.04. Unfortunately, upgrading to a newer version of ubuntu is not an option for this device.

Here is the issue I'm having: sometimes when I connect to the public FTP it connects right up and stays connected for a while. Sometimes it won't connect at all. Last night I had to connect via samba since FTP wouldn't work at all.  The server we are connecting to was recently upgraded from Windows Server 2003 to Windows Server 2012 R2. Currently we have other Ubuntu machines running 10.04, 13.10, and 14.04 and they all connect to the FTP without issues.  I'm wondering if this version of Ubuntu requires something special in the server config side?

I have tried installing Filezilla as a workaround, and wasn't able to get it to install.

---

### Post by sudodus on 2014-12-16
Ubuntu 8.04 passed end of life many years ago. You can't expect everything in it to work now, and you can't expect it to be possible to update. Furthermore it is open for attacks, when connected to the internet. Please install a current version of a linux distro (Ubuntu based if possible) in that computer. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

---

### Post by chris330 on 2014-12-16
I would love to upgrade it, but it's a specialized image to work with a specific device. I asked the manufacturer of this device months ago to upgrade it, and there are no plans to do so. So we're kind of stuck.

Are you saying that this is a compatibility issue, and there's nothing we can do or tweak?

---

### Post by sudodus on 2014-12-16
I think it is a compatibility issue, but it might be possible to solve, if you get good help. I don't know how to do it, but there are people, who know a lot about networking and tools for it, and also people who might help you to port a newer version of ftp to 8.04.

---

