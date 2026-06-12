---
title: "Strange GUI behaviour on 10.04"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by garethrevo on 2010-11-17
I installed 9.10 with the Netbook remix edition on an Acer Revo R3600 to run my Squeezebox server - so far so good. The machine was left running with no connected monitor, mouse or keyboard which is how I want it.

The remote desktop connection didn't work well, as it froze after a minute or so being connected, so I used X11VNC over SSH and could get the remote GUI working acceptably well. I'm not good with the CLI, so this was useful for me.

I upgraded to 10.04 via this remote connection - possibly a mistake - and ever since, when I connect to see the GUI, every window I open stays on top for a second or two, then disappears. Applications are still on the task bar, but I can't use anything. 

I've now tried this with directly connected monitor mouse and keyboard, and it behaves in exactly the same way, so not VNC related.

SSH still works fine for a CLI which I can use to run updates.

I can't find any other references to similar problems. Any ideas before I reinstall everything - probably without the Netbook remix/edition 

Thanks in advance

---

### Post by sikander3786 on 2010-11-17
Do all the windows disappear after a few seconds?

Try open some of them from the terminal and post the output e.g, for File Browser type,

```
nautilus
```

What is the output when it disappears?

Might be you've got some broken packages. So trying these commands won't hurt.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by nothingspecial on 2010-11-17
Have you tried ssh -X

Does that work?

---

### Post by nothingspecial on 2010-11-17
As you are doing this to run squeezeboxserver, as I do, perhaps ust some familiarity with a few commands would be of use.

The only things I ever use (for the squeezeboxserver) is abcde, scp and the rescan command which I have aliased.

So if I want to send some music to the server

```
scp -rv /path/to/the/music ns@192.168.1.7:Music/
```

If I want to rip a cd I use abcde

you can find some prewritten config files by andrew46 (might be 42) here

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I have the ogg one and flac one saved in my home as .abcde_ogg.conf and .abcde_flac.conf and tell abcde which one to use, you can modify them and they are well documented.

Here is the section of my .bashrc concerned with this

```
#Cd ripping
alias cd2flac='abcde -c ~/.abcde_flac.conf'
alias cd2ogg='abcde -c ~/.abcde_ogg.conf'

#Rescan squeezeboxserver
alias scan='echo -e "rescan\nexit\n" | nc localhost 9090'
```

So, as you can see if I want to rip to flac I just type ```
cd2flac
```

or if I want to rescan the server ```
scan
```

Have a go, then you w2on`t even need a gui at all.

---

### Post by garethrevo on 2010-11-17
All the windows disappear, even terminal, so I can't launch anything from the command line.

Did both the apt-get and dpkg commands aboe, but nothing changed.

I did try to check the Nvidia settings and saw a message that indicated the drivers weren't being used, and to configure it via the command line. I think this could be helpful, so I'm going to give it a try now.

Thanks for the quick response

---

### Post by garethrevo on 2010-11-17
> **nothingspecial said:**
> As you are doing this to run squeezeboxserver, as I do, perhaps ust some familiarity with a few commands would be of use.

The only things I ever use (for the squeezeboxserver) is abcde, scp and the rescan command which I have aliased.

So if I want to send some music to the server

```
scp -rv /path/to/the/music ns@192.168.1.7:Music/
```

If I want to rip a cd I use abcde

you can find some prewritten config files by andrew46 (might be 42) here

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I have the ogg one and flac one saved in my home as .abcde_ogg.conf and .abcde_flac.conf and tell abcde which one to use, you can modify them and they are well documented.

Here is the section of my .bashrc concerned with this

```
#Cd ripping
alias cd2flac='abcde -c ~/.abcde_flac.conf'
alias cd2ogg='abcde -c ~/.abcde_ogg.conf'

#Rescan squeezeboxserver
alias scan='echo -e "rescan\nexit\n" | nc localhost 9090'
```

So, as you can see if I want to rip to flac I just type ```
cd2flac
```

or if I want to rescan the server ```
scan
```

Have a go, then you w2on`t even need a gui at all.
Thanks for the CLI info - I can generally do what I need via the web interface for Squeezeserver. I'm doing ripping on  Win XP box anyway, and then syncing content over for Squeezeserver to scan/index. This bit works fine !

---

### Post by garethrevo on 2010-11-17
> **nothingspecial said:**
> Have you tried ssh -X

Does that work?

I'm using putty from a Win XP box, so not sure how I'd do that. There is an option under X11 for SSH which is to enable X11 forwarding, but this doesn't seem to help.

I'm starting to think I will do a clean install at some point...

---

### Post by nothingspecial on 2010-11-17
I`ve no idea how it works from windows but if you

```
ssh -X user@ipaddress
```

Then type ```
gnome-panel
```

You can click away.

---

