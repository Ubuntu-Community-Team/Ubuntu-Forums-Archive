---
title: "To google or chm?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by degarb on 2011-01-16
My approach with Ubuntu has been to google for minimum 20 minutes, try stuff, then post is needed.   Most googled stuff leaves out key points, is old. I have used programming languages that are easier to pickup and write programs with than linux.  Really.
Googling windows issues are far easier for what ever reason than linux. 

I am thinking I have it all backwards.  Maybe I should install some knowledge tree ap and search it first, or is there some chm that I am missing, or some knowledge base/launchpad or another?  

---
(launch pad search for how to add user in samba: first one is wrong and second has way, but fails to tell us if we need to stop samba to add.  
sudo smbpasswd -a <username>
New SMB password: ######
Retype new SMB password: ######
didn't work on my last attempt.  But samba wasn't stopped, since no google brought up how.  }

---

### Post by 123456789123456789123456 on 2011-01-16
I've never really had a problem googling help with certian topics, problems or even command line commands.

what help were you searching for?  How did you google it?

it is possible you were wording the question the wrong way, it took me a little time to figure out how to do it myself.

---

### Post by libssd on 2011-01-16
> **degarb said:**
> My approach with Ubuntu has been to google for minimum 20 minutes, try stuff, then post is needed.   Most googled stuff leaves out key points, is old. I have used programming languages that are easier to pickup and write programs with than linux.  Really.

[LIST=1]
[*] When googling for Ubuntu information, use site:[http://ubuntuforums.org/](http://ubuntuforums.org/) to limit your search to this site. That should give you more relevant information. **OR**, use [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

[*] For documentation, start here: [https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

[*] For a more traditional guide to Ubuntu, you might want to download *Ubuntu Pocket Guide and Reference*, by Keir Thomas.
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

[*] When in terminal, man followed by a command name will generate the documentation for that command.

[*] If you are not yet comfortable with the command line, read this: [https://help.ubuntu.com/community/CommandlineHowto?action=show&redirect=CommandLine](https://help.ubuntu.com/community/CommandlineHowto?action=show&redirect=CommandLine)
[/LIST]

---

### Post by 3rdalbum on 2011-01-16
When using Google, type in the version of Ubuntu you are using and don't follow old tutorials.

For your Samba query, I'd recommend using one of the available frontends for Samba that makes it easy to set up. There's "system-config-samba" in the repositories, or you can type "gksudo shares-admin" into the terminal for the built-in one.

---

