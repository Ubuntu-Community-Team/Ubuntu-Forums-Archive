---
title: "second life issue"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by hookitup on 2011-08-22
hello ppl, so im  trying to play the game second life on my ubuntu laptop, its a Dell Latitude E6400, 
im running ubuntu 11.04, i downloaded it from [this sit  ]("http://secondlife.com/support/downloads/?lang=en-US")and the extracted it then run the install through the terminal and that didnt work because it wont do anything when i go to unity and open second life, so i tried to run it straight from the directory "second life" and also that didnt work because when i run it the screen flickers and the second life  windows opens for a split second then disappears. i dont really see any errors in the terminal , maybe this means something ```
This is a BETA release of the Second Life linux client.
Thank you for testing!
Please see README-linux.txt before reporting problems.

dark@darkmyth:~/Downloads/SecondLife-i686-2.8.3.238392$ 2011-08-22T15:59:17Z INFO: (anonymous namespace)::LogControlFile::loadFile: logging reconfigured from /home/dark/Downloads/SecondLife-i686-2.8.3.238392/app_settings/logcontrol.xml
[COLOR=Red]2011-08-22T15:59:17Z WARNING: ll_apr_warn_status: APR: No such file or directory
2011-08-22T15:59:17Z WARNING: remove:  Attempting to remove filename: /home/dark/.secondlife/logs/SecondLife.exec_marker[/COLOR]
2011-08-22T15:59:17Z INFO: updateApplication: Gathering logs...
2011-08-22T15:59:17Z INFO: gatherFiles: Using log file from debug log /home/dark/.secondlife/logs/SecondLife.log
2011-08-22T15:59:17Z INFO: gatherFiles: Using settings file from debug log /home/dark/.secondlife/user_settings/settings.xml
2011-08-22T15:59:17Z INFO: updateApplication: Encoding files...
[COLOR=Red]Can't find file /home/dark/.secondlife/user_settings/settings.xml
Can't find file /home/dark/.secondlife/logs/stats.log[/COLOR]
2011-08-22T15:59:17Z INFO: updateApplication: Sending reports...
2011-08-22T15:59:17Z INFO: updateApplication: Sending to server, try 1...
2011-08-22T15:59:17Z INFO: run: thread_error - Waiting for an error
2011-08-22T15:59:17Z INFO: main: Crash reporter finished normally.
2011-08-22T15:59:17Z INFO: ll_cleanup_apr: Cleaning up APR

```maybe the stuff in the red means something, not quiet sure what to make of it, 

i have also tried to install my graphic drivers (thinking that was the issue) , that was not successful when fallowing [this websit]("http://eddieringle.com/how-to-install-official-nvidia-drivers-in-linux/")..... got tons of errors , i have also check [this out ]("https://help.ubuntu.com/community/CompilingEasyHowTo")not 100% sure if this is necessary, i feel it is more a issue with the video card possibly, i run ```
lspci -v | less
``` and got ```
0:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Dell Device 0233
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 0233
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at ef98 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Dell Device 0233
        Flags: bus master, fast devsel, latency 0
:

```
any help ? id very much appreciate it. Thanks

---

### Post by Matt__ on 2011-08-22
Such integrated gfx are not made to run 3d games. try googling second life gma 4500hd and see.

Even if you do get it running (try [Phoenix Viewer]("http://www.phoenixviewer.com/downloads.php")) it will be pretty gutless, laggy, glitchy, slow to render even using the lowest graphics settings + tweaking from the advanced menu.

Or maybe try something based on V1 viewer like [Singularity viewer]("http://wiki.secondlife.com/wiki/Third_Party_Viewer_Directory/Singularity") or [cool viewer VL]("http://sldev.free.fr/"). (it will still run badly :) )


a 2007 post on how badly sl runs on dell 6400 with gma 4500 [http://forums-archive.secondlife.com/111/51/320434/1.html](http://forums-archive.secondlife.com/111/51/320434/1.html) and it will only have got worse since then as sl gets more gfx hungry.


#speaking from experience with assisting users at university where media and fashion programs used SL as part of the curriculum.

---

### Post by sleepingdragon on 2011-08-22
Oddly, I get better results using the Windows version of SL under WINE, but both (Win/Lin) still crash out for me. For some reason everything grinds down to about 1 fps after about 10 minutes, with no idea how to fix it. 

Peronsally, I think SL's 3D implementation sucks. I can hammer out 3D games with some pretty decent quality, but SL seems to be slow and clumsy.

---

### Post by Overcast32 on 2011-08-22
That's a native Second Life client.. interesting. It's been quite a while since I've even looked at that game - ran it under windows for a while.. 

But.. 

```
Can't find file /home/dark/.secondlife/user_settings/settings.xml
Can't find file /home/dark/.secondlife/logs/stats.log

```

Does that path exist? "/home/dark/.secondlife"

Would be hidden of course, see if 'dark' is the owner of '.secondlife' and not root?

---

### Post by hookitup on 2011-08-22
> **Overcast32 said:**
> That's a native Second Life client.. interesting. It's been quite a while since I've even looked at that game - ran it under windows for a while.. 

But.. 

```
Can't find file /home/dark/.secondlife/user_settings/settings.xml
Can't find file /home/dark/.secondlife/logs/stats.log

```Does that path exist? "/home/dark/.secondlife"

Would be hidden of course, see if 'dark' is the owner of '.secondlife' and not root?
its in my downloads under dark....

and for everybody else , ok thanks for the heads up ,,, ill try some of thoes other viewers

---

### Post by sleepingdragon on 2011-08-22
The Linux version of SL [from their site]("http://download.cloud.secondlife.com/beta-releases/Viewer-3/SecondLife-i686-3.0.1.238613.tar.bz2") does offer a proper installation - menu entry, /home/user/.secondlife folder, etc. I seem to have one and it does work well... until I hit 1 fps. Extract the tar file and run the install.sh file.

NOTE: The link is for the beta v3.0 SL viewer. v2.8 just seems too buggy for my liking. I've also just seen their recommended graphics hardware - nVidia 9600/9800 - ouch!

---

### Post by Overcast32 on 2011-08-22
> **hookitup said:**
> its in my downloads under dark....

and for everybody else , ok thanks for the heads up ,,, ill try some of thoes other viewers

Well, you can try those - but if you choose to hack it out on this one.. 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

ls -la /path/to/file

Might show something similar to:

```
-rwxr--r-- 1 dark dark 300 Aug 18 12:11 .secondlife
```

Should show you as the owner, if that doesn't seem to work, do a 'ls -lisa' in the home folder. This is just a 'first test' kinda thing you can do to check file permissions. Or yeah - right click in Nautilus and check permissions works too. :o

See if the '.secondlife' folder shows 'root root' or 'dark dark'. 

```
-rwxr--r-- 1 root root 300 Aug 18 12:11 .secondlife
```

You want it to show 'dark' otherwise, it will get permission issues running as you and I wouldn't advise running a game client as root - too many potential problems/questions about running with that kinda access.

It *should* say 'dark' there now (if that's the account you are using, I'm just guessing from the home folder name) as it should have inherited permissions from your home folder root, but it doesn't mean that app installed right, or if you installed a root, it might do that too.

---

### Post by hookitup on 2011-08-23
> **Matt__ said:**
> Such integrated gfx are not made to run 3d games. try googling second life gma 4500hd and see.

Even if you do get it running (try [Phoenix Viewer]("http://www.phoenixviewer.com/downloads.php")) it will be pretty gutless, laggy, glitchy, slow to render even using the lowest graphics settings + tweaking from the advanced menu.

Or maybe try something based on V1 viewer like [Singularity viewer]("http://wiki.secondlife.com/wiki/Third_Party_Viewer_Directory/Singularity") or [cool viewer VL]("http://sldev.free.fr/"). (it will still run badly :) )


a 2007 post on how badly sl runs on dell 6400 with gma 4500 [http://forums-archive.secondlife.com/111/51/320434/1.html](http://forums-archive.secondlife.com/111/51/320434/1.html) and it will only have got worse since then as sl gets more gfx hungry.


#speaking from experience with assisting users at university where media and fashion programs used SL as part of the curriculum.
 

the phoenix viewer worked,,,


thanks

---

