---
title: "Install on old computer"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Kip-a-fied on 2011-08-24
I was given an old gateway with all the system requirements for xubuntu. I made a cd-r of xubuntu and popped it in. Here's the problem, when I try to Try out Xubuntu or Install it, I get a screen with the following code

[ 17.669534] [<c1126940>] ? do_sync_write+0X0/0xe0
[ 17.669608] [<c1127482>] ? sys_write+0x42/0x70
[ 17.669687] [<c178f777>] ? do_copy+0x81/0x9c
[ 17.669775] [<c178f368>] ? write_buffer+0x1d/0x2c
[ 17.669863] [<c178f3cf>] ? flush_buffer+0x58/0x71
[ 17.669950] [<c178f21a>] ? error+0x0/0x13
[ 17.670047] [<c17b3f0c>] ? unlzma+0x467/0x544
[ 17.670136] [<c17b33c9>] ? nofill+0x0/0x8
[ 17.670222] [<c178f21a>] ? error+0x0/0x13
[ 17.670306] [<c178f377>] ? flush_buffer+0x0/0x71
[ 17.670395] [<c17b3aa5>] ? unlzma+0x0/0x544
[ 17.670483] [<c178ffbc>] ? unpack_to_rootfs+0x165/0x270
[ 17.670571] [<c178f377>] ? flush_buffer+0x0/0x71
[ 17.670658] [<c178f21a>] ? error+0x0/0x13
[ 17.670744] [<c1790115>] ? async_populate_roots+0x4e/0xcb
[ 17.670849] [<c1074bf9>] ? async_run_entry_fn+0x69/0x170
[ 17.670941] [<c10688ae>] ? process_one_work+0xfe/0x360
[ 17.671047] [<c1067d0a>] ? maybe_creat_worker+0xda/0xe0
[ 17.671137] [<c1074b90>] ? async_run_entry_fn+0x0/0x170
[ 17.671227] [<c1068e34>] ? worker_thread+0x124/0x2d0
[ 17.671315] [<c1068d10>] ? worker_thread+0x0/0x2d0
[ 17.671413] [<c106ce04>] ? kthread+0x74/0x80
[ 17.671501] [<c106cd90>] ? kthread+0x0/0x80
[ 17.670646] [<c100367e>] ? kernel_thread_helper+0x6/0x10

then a blinking _ for hours. I re-burned the disc same thing comes up. I even switched the hard drive. Any help is greatly appreciated. 

Ps, I want to learn more about linux, recommend any good books?

---

### Post by sffvba[e0rt on 2011-08-24
From this thread ([http://ubuntuforums.org/showthread.php?t=1640299](http://ubuntuforums.org/showthread.php?t=1640299)) it seems that the alternative CD image for Ubuntu (and thus Xubuntu) may do the trick... So just go to any of the mirrors and download the image labeled alternative and not desktop and try that one...


404

---

### Post by MG&amp;TL on 2011-08-24
Can't help for your 'puter, but I find that chucking myself in at the deep end is often a good thing, so I recommend as an all-in-one measure 'Linux in a nutshell' from O'reilly. Heavy, but good stuff. Just make sure any commands apply to ubuntu first.

Of course, there are many online tutorials sites, some quite extensive. I can link to some of those if you would like, depending on what you want to learn about. 'Linux' is a big topic. :P

---

### Post by Kip-a-fied on 2011-08-24
@not found - Thanks Dude! I'm downloading the alternative now.

@MG&TL - I to do try to explore the deepest tunnels, I just need a flash light to help sometimes. I would like to learn how to run wireless home network with roaming profiles, Basic IT knowledge, and programming. I'm 26 and my family raised me on windows 98, xp, 7 and server 08 and I like using ubuntu and love the GPL and what open source stands for. I'm ready to switch my alliance head on! I wanna be a linux head and help convert!

---

### Post by MG&amp;TL on 2011-08-24
First of all, do you know how to use a terminal?

[http://linuxcommand.org/]("http://linuxcommand.org/") will take you through BASH (the linux equivalent of cmd) and bash scripting (.bat files for linux, kinda).



For Ubuntu knowledge in general, try the ubuntu documentation:

[https://help.ubuntu.com/]("https://help.ubuntu.com/")

and the Ubuntu wiki:

[https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")




Programming, there's lots of languages, but try GNU for various tools and tips (although it's not exactly user-friendly, and you need to ignore quite a lot of stuff about their OS):

[http://www.gnu.org/]("http://www.gnu.org/")

And once you've written a program, if you want to distribute it, you need to package it for Ubuntu, 'basic' method :

[http://ubuntuforums.org/showthread.php?t=910717]("http://ubuntuforums.org/showthread.php?t=910717")

and 'argghhh...do it like this to get it in ubuntu repos or launchpad' method:

[https://wiki.ubuntu.com/PackagingGuide]("https://wiki.ubuntu.com/PackagingGuide")





And there's lots of network tools already built-in to ubuntu, but if you need more, get it from the software centre, apt-get, synaptic, or wherever. 

If you need help on a command, type 

```
man <your problem command here>
```


or sometimes

```
<command here> --help
```

In a terminal.

Have fun. And don't complain that your brain melted. :D

---

### Post by kmsalex on 2011-08-25
what exactly are those specks?

---

### Post by sidzen on 2011-08-25
Go to [Granddaddy]("http://www.slackbook.org/") and ask!

+1 to the one from *New Joisey*

---

