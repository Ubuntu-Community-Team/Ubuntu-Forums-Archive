---
title: "getting prompt in virtualbox from rails"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by gmyuser on 2010-11-25
I run ubuntu in virtualbox on windows and have installed rails. The problem now is that when  I load up the virtualbox it goes straight to load rails and asks for my user name and password. I use root and xxxx. So I have the prompt root@rails.

I go on installing lots of things, but I have a feeling that I am not installing at the root. When I try using sudo it says command not found, so I don't use sudo.
I want to load some files like rubygems, so I downloaded them and made a shared folder for them that I added properly and then made a directory. But when I try the command:

mount -t vboxsf folder-name /media/windows-share

I get the response: unknown filesystem type vboxsf

How can I get this kind of command to work? Am I executing from the wrong place?

---

