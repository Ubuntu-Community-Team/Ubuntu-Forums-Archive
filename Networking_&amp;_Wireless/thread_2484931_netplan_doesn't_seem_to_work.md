---
title: "netplan doesn't seem to work"
date: 2023-03-14
forum: Networking &amp; Wireless
---

### Post by banci on 2023-03-14
Hi guys,


I'm not a newbie but it has passed some years since I last used Ubuntu so I forgot most of it. :(

I am currently using Ubuntu **22.04.2** on-boarded on **Windows WSL2**.

My current concern is that I'm not sure whether I setup everything ok. I created **01-config.yaml** file with some content, however when I run ***sudo netplan apply*** I don't see any changes in my networking. ](*,)

There are also two files in /usr/lib/netplan - **generate **and **netplan-dbus**. Should I put some commands in there?

My **Netplan.io** file is up-to-date.


Thanks in advance for any help, banci.

---

### Post by TheFu on 2023-03-16
Please prove all the claims above by posting the output of config files and commands. Whenever posting, please wrap the output in forum 'code tags'. The "Adv Reply" button with a # makes doing that trivial. It will make reading the output 100x easier.

People make claims all the time, because they believe they understand more than they do or just don't really understand the output. Often, gathering the proof, will make it clear where the issue lies.

BTW, I don't know anything about WSL2 or WSL.  I don't know what black magic they've decided to use to make it work or how, if at all, they handle networking.  My understanding is that is MSFT's attempt to derail people from having a full Ubuntu Server experience like you'd have running a virtual machine.  Most people aren't prepared for the CLI-only experience that are Linux servers (no GUI).

I'm only replying so you know someone actually read your post.  Someone else with WSL knowledge will need to reply with any help. Posting the files and commands (inside code-tags) will help them to help you.

---

### Post by banci on 2023-03-20
Thanks for the hint TheFu. If there won't be any useful suggestions to my issue I will probably switch to having Ubuntu on 'normal' hosting system and not on WSL. I decided for WSL as I thought it as I good idea to avoid installing VM.

---

### Post by TheFu on 2023-03-20
[https://learn.microsoft.com/en-us/windows/wsl/faq](https://learn.microsoft.com/en-us/windows/wsl/faq) says that a stripped down hypervisor is provided by WSL, so it is definitely running a VM.  OTOH, they don't need any audio or video stuff which is the most complex part to any hypervisor for support.  If you strip though out of the settings for a VM, then it will be fast and light too.
The only thing that might be great is that from WSL, Windows programs can be run too.  There have been times when that would be handy. I've usually ended up creating a Win32 Perl script to do that when needed, using Strawberry Perl.  Strawberry Perl "feels" like perl on a Unix system, unlike Active State's Perl on Windows.  Which would be preferred would likely depend on which platform is more comfortable.  BTW, I was a cross-platform C++ developer for a decade.  Windows development tools make it hard NOT to use proprietary, Windows-only, libraries.

---

