---
title: "Files shared with samba appear to be empty from Ubuntu 12.04"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by yeswekey2 on 2013-11-02
I'm trying to create a symlink to a Samba share so that I can work remotely on a rails app.

However all the files appear empty as seen in the cat command. I even tried opening with nautilus to connect (the normal way) and still all files appear empty when I open them with gedit. I have XP running in VirtualBox. I'm able to see/edit all the shared files/folders from the virtual XP (using SMB, not VBoxSharedFolderFS), but not from my host OS Ubuntu 12.04 64-bit! 

```
kaushik:~$ ln -s ~/.gvfs/_confidential_\ on\ macbookpro-4303/ _confidential_
kaushik:~$ cd _confidential_
kaushik:_confidential_$ cd my_subdir
kaushik:my_subdir$ ls
app  config  db  deploy  doc  dump.rdb  Gemfile  Gemfile.lock  integrations  lib  LICENSE  log  mobile  omnitmp  public  Rakefile  README  script  spec  test  tmp  vendor
kaushik:my_subdir$ cat Gemfile
kaushik:my_subdir$ 

```


Any help is appreciated coz I'm desperately looking for a solution. Thanks in advance.

---

### Post by yeswekey2 on 2013-11-03
*bump*
Help plz :(
I was initially getting some error like application can't be found. But now they appear empty.  Also tried accessing from a laptop with xp. The problem occurs only in my Ubuntu PC. Tried restarting ma machine several times but it was of no use. I'm clueless. Plz help. Thanks in advance :D

---

### Post by Jens2 on 2014-02-05
Hi,
did you ever solve this? I have the same problem (files shared from a Mac, running Mountain Lion 10.8.5).
Thanks!

---

### Post by yeswekey2 on 2014-02-06
Hi jens2,
No I couldn't resolve it. I too used Mountain Lion 10.8.x by the way. My guess is that we need to setup Network File System and mount it on Ubuntu. Wasn't worth the effort so I thought I can just RDP my mac and work, or work on mac itself..!! Please share if you come across any other solution.
Thanks!

---

