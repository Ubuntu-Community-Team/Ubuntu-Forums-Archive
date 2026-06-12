---
title: "How to change permissions"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by bj218 on 2011-05-30
How do I change permissions I am the only one that uses this computer?
See the attachment. How do I change roor to bill?

---

### Post by Andreawws on 2011-05-30
root owns it you cannot without root privileges

---

### Post by bj218 on 2011-05-30
> **Andreawws said:**
> root owns it you cannot without root privileges

I do not understand since I am the only one to use computer I thought
I was root!!

---

### Post by The Cog on 2011-05-30
Currently, root is the owner of this file. Only root can change the ownership of files. You can temporarily use root's credentials with **sudo** - see this link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You say that you want to change the owner to bill. You should only do this with files that resided inside bill's home directory (inside /home/bill). All of user bill's files should be kept inside his home directory. This is true even if bill is the only user. Files outside the /home directory should be regarded as system files, and you should not be tinkering with them.

---

### Post by dFlyer on 2011-05-30
Your not root. You have root access with sudo. If you don't know what your doing, my advice is to get a book and read up on linux. It doesn't matter if your the only user or not. If you connect to the internet and your root your at risk you system will be totally exposed. You might as well be running Windows.

---

### Post by JKyleOKC on 2011-05-30
Is the file in your home directory (the place that you land when you log in), or is it on a USB stick or a Windows machine accessed through a network?

Since it shows "root" as the file owner, and has execute permission even though the file appears to be from OpenOffice, I'd bet on the latter case. If this is the situation, the simplest solution would be to copy the file into your home folder. That would automatically make you the owner and allow you to change its permissions.

If it's already in your home folder, you can change its ownership by using the terminal commands but I'll hold off on telling you about them until you reply; I don't want to scare you. If it's elsewhere on your hard drive, it may be one that you should not be changing.

One of the reasons that Ubuntu is in general more secure than Windows is that it has the system of permissions. They not only protect you against invaders, but against yourself. All of us, I think, have occasionally fat-fingered a file that we should not have, with somewhat disastrous results. The permissions force you to think twice when dealing with such a file, yet are designed so that they do not get in your way most of the time.

Dealing with files on a USB stick or a Windows box is, however, an exception to that design rule. Since the Windows file formats do not have such fine-grained permissions, the system must assign them somewhat arbitrarily -- and erring on the side of safety, you get them opened as "read-only" and cannot easily change them!

---

### Post by Andreawws on 2011-05-30
I personally went this way:
I use a 'command' (Not telling you what since it would be a security breach to have a password for root, and because you could REALLY **** up) to add a pass for root
then I do whatever I am going to do (Only when I am going to do a lot of stuff)
Then I go back and remove the pass with a similar 'command'

---

### Post by The Cog on 2011-05-30
> **bj218 said:**
> I do not understand since I am the only one to use computer I thought
I was root!!

No, I guess from your post that you are bill. root is the account that is (I think) the equivalent of the system account in windows. As my last post said, you can use sudo to "borrow the keys" when you are doing system administration, but you should not log in as root - should not working as root except for those administration tasks. For safety, from both exploits/trojans and from mistakes on your part (see all the posts saying I accidentally deleted all of some system folder).

---

### Post by bj218 on 2011-05-30
> **JKyleOKC said:**
> Is the file in your home directory (the place that you land when you log in), or is it on a USB stick or a Windows machine accessed through a network?

Since it shows "root" as the file owner, and has execute permission even though the file appears to be from OpenOffice, I'd bet on the latter case. If this is the situation, the simplest solution would be to copy the file into your home folder. That would automatically make you the owner and allow you to change its permissions.

If it's already in your home folder, you can change its ownership by using the terminal commands but I'll hold off on telling you about them until you reply; I don't want to scare you. If it's elsewhere on your hard drive, it may be one that you should not be changing.

One of the reasons that Ubuntu is in general more secure than Windows is that it has the system of permissions. They not only protect you against invaders, but against yourself. All of us, I think, have occasionally fat-fingered a file that we should not have, with somewhat disastrous results. The permissions force you to think twice when dealing with such a file, yet are designed so that they do not get in your way most of the time.

Dealing with files on a USB stick or a Windows box is, however, an exception to that design rule. Since the Windows file formats do not have such fine-grained permissions, the system must assign them somewhat arbitrarily -- and erring on the side of safety, you get them opened as "read-only" and cannot easily change them!

What I am trying to do is take a lot of very helpful responses to ? I have asked on the Internet & put them on paper so that I can refer to 
them easily & not have to remember where they are located on my computer.
Most of these items are located on a separate partition called miscu 
but some are located in home/bill. I have been putting these on an Open Office doc called MY NOTES which has gotten into some bad trouble in the last few days any help would be much appreciated.

---

### Post by JKyleOKC on 2011-05-30
Is your Open Office document stored in your home folder? And is it the one that shows "root" as its owner?

If the answer to both of these questions is "Yes" then here's how to fix it: Open the terminal and type in the following line, replacing "MY NOTES.odt" with the actual file name if it's different.```
sudo chown bill.bill "MY NOTES.odt"
```You'll be asked for your password; it's the same as the one you use to log in, and you won't see any indication at all that you've typed it but trust us, it's going into the program. Be sure that the file name is exactly what your file is named, and don't omit the quote marks -- they are what keep the command line shell from seeing the space between MY and NOTES.

If it's not in the home folder but is in a subfolder such as Documents, change to that directory before doing the above.

That ought to be all that you need to do; you should then have full write permission and not need to change anything else at all!

---

### Post by oldfred on 2011-05-31
What format is miscu? And how are you mounting it. Default mount may not give you all the permissions & ownership you want:

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by bj218 on 2011-06-01
I'M in big trouble!! Yesterday I connected 2 HD's in my system. I now have
a serial drive & 2 parallel drives. One of the parallel drives had 
ubuntu on it the other had WinXP the serial drive was blank. When I tried to started up the system I got nothing on my 2nd try at startup I found that I had only 1 drive the serial drive. In desperation I installed 
ubuntu on it & thats where I am at this time. At the moment I'm at a total lose as to what I should do next.One thing I know is that I can't continue with the problem we were working on. THANKS TO ALL

---

### Post by AlphaLexman on 2011-06-01
Also see this about being root and having root privileges.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by I'mGeorge on 2011-06-01
the best most comprehensive way to change permissions in linux is using chmod in command line.

```

u - user or owner				chmod u+w file1
g - group					-adds write permission for the user
o - others    					chmod +w file1
a - all                            <Exemple>    -adds write permission for the user, group and others
						chmod go-x file1
r - read permission				-deletes execute permission for the group and others	
w - write permission				chmod u=r file1	
x - execute permission				-changes the permissions for the user to be just read
						 permission (group and other permissions are not changed)

```

you can also use numbers instead of letters while changing permissions through chmod, but letters are more easy to understand therefore reducing the possibility of mistakes

---

