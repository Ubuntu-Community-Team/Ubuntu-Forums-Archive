---
title: "Chromium Browser Lucid"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-30
Hey all, just completed my upgrade to 10.04 all went fine, so far it's working flawlessly, even some small issues I had with Karmic have been corrected, the only victim of this upgrade has been the Chromium Browser..it doesn't start, when I click the icon it does nothing, I tried reinstalling from synaptic still nothing, any ideas? I really like this browser....THX

---

### Post by phrostbyte on 2010-04-30
Try running it in a terminal (I think the command is "chromium" or "chromium-browser") and paste the output.

---

### Post by uRock on 2010-04-30
```
chromium
```

---

### Post by swoll1980 on 2010-04-30
If none of that works try purging it. 
```
sudo dpkg -P chromium-browser
```
then log out, back in, reinstall, and see.

---

### Post by jnmjr on 2010-04-30
> **phrostbyte said:**
> Try running it in a terminal (I think the command is "chromium" or "chromium-browser") and paste the output.

All it says is command not found or illegal instruction.

---

### Post by jnmjr on 2010-04-30
> **swoll1980 said:**
> If none of that works try purging it. 
```
sudo dpkg -P chromium-browser
```
then log out, back in, reinstall, and see.

jose@My-Desktop:~$ sudo dpkg -P chromium-browser
[sudo] password for jose: 
dpkg: dependency problems prevent removal of chromium-browser:
 chromium-browser-inspector depends on chromium-browser.
 chromium-codecs-ffmpeg depends on chromium-browser (>= 4.0.203.0~).
dpkg: error processing chromium-browser (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 chromium-browser

Doesn't want to uninstall... Should I try to uninstall dependencies from Synaptic?

---

### Post by phrostbyte on 2010-04-30
Do what the package purge thing that swoll1980 said and try to reinstall it afterwords. If that doesn't work do this and paste the output:

```

which chromium 
which chromium-browser
dpkg -l | grep chrom

```

What I am trying to see is if you have it installed and it is corrupted, or its just didn't get installed at all.

---

### Post by phrostbyte on 2010-04-30
Try using Synaptic if you can, try "right-click" and complete removal.

---

### Post by swoll1980 on 2010-04-30
try 
```
sudo apt-get upgrade --fix-missing
```

---

### Post by swoll1980 on 2010-04-30
If all else fails computer janitor is your friend.

---

### Post by jnmjr on 2010-04-30
> **swoll1980 said:**
> try 
```
sudo apt-get upgrade --fix-missing
```

> **swoll1980 said:**
> If all else fails computer janitor is your friend.

Nothing has worked so far, I don't understand.

---

### Post by swoll1980 on 2010-04-30
> **jnmjr said:**
> Nothing has worked so far, I don't understand.

Computer janitor helps you clean up lost programs. system> administration> computer janitor use it to remove chrome. If it gives you the option too.

---

### Post by ddecator on 2010-04-30
If you still have the chromium-browser package installed, can you try running it in a terminal? It's 'chromium-browser' (I believe just 'chromium' is used by the Chromium BSU game). The output from that can help us figure out what's wrong =)

---

### Post by jnmjr on 2010-04-30
> **ddecator said:**
> If you still have the chromium-browser package installed, can you try running it in a terminal? It's 'chromium-browser' (I believe just 'chromium' is used by the Chromium BSU game). The output from that can help us figure out what's wrong =)

I deleted it through Synaptic..... I'm going to bed... Sorry guys I'll pick up tomorrow...THX for your help so far

---

### Post by jvc26 on 2010-04-30
Do you have the karmic repository still in your sources.list? 

```
sudo add-apt-repository ppa:chromium-daily/beta
```

Will add the chromium ppa and point it at the right sources, but you should remove the old version from your sources.list either manually or via System->Administration->Software Sources.

J

---

### Post by Toost Inc. on 2010-04-30
I´m having the same problem. Only I think the problem started BEFORE upgrading to Lucid (only slightly though).

But anyway, tried purging and reinstalling it but that didn´t help. 

As for extra information, using version 5.0.391.0~svn20100428r45775-0ubuntu1~ucd2 (latest at the time of posting this as far as I know) and I´m also using the non-free (extra) version of the ffmpeg codecs though I did try it with just the free ones, which gave the same results

---

### Post by jnmjr on 2010-04-30
> **jvc26 said:**
> Do you have the karmic repository still in your sources.list? 

```
sudo add-apt-repository ppa:chromium-daily/beta
```

Will add the chromium ppa and point it at the right sources, but you should remove the old version from your sources.list either manually or via System->Administration->Software Sources.

J

> **Toost Inc. said:**
> I´m having the same problem. Only I think the problem started BEFORE upgrading to Lucid (only slightly though).

But anyway, tried purging and reinstalling it but that didn´t help. 

As for extra information, using version 5.0.391.0~svn20100428r45775-0ubuntu1~ucd2 (latest at the time of posting this as far as I know) and I´m also using the non-free (extra) version of the ffmpeg codecs though I did try it with just the free ones, which gave the same results

Hey guys, I've got the repo, no problem, I got the same issue after re-installing it may well be a problem with the latest release and not an OS issue, right now we need more people to who use Chromium to post if they are having the same problem or if they've found the solution...THX :confused:

---

### Post by bOR_ on 2010-04-30
Same problem as Toost, (also starting some days before installing lucid). Running a relatively old mobile AMD athlon xp, getting the following when I do 

chromium-browser -g
(gdb) start

Temporary breakpoint 1 at 0x806cbd8: file chrome/app/chrome_exe_main_gtk.cc, line 28.
Starting program: /usr/lib/chromium-browser/chromium-browser 
[Thread debugging using libthread_db enabled]

Program received signal SIGILL, Illegal instruction.
0x0859b6ae in tcmalloc::SizeMap::NumMoveSize (this=0xa1b2020, size=8) at third_party/tcmalloc/chromium/src/common.cc:59
59	third_party/tcmalloc/chromium/src/common.cc: No such file or directory.
	in third_party/tcmalloc/chromium/src/common.cc
(gdb) 


I did do the computer janitor thing, and the fix missing.

---

### Post by jnmjr on 2010-04-30
> **bOR_ said:**
> Same problem as Toost, (also starting some days before installing lucid). Running a relatively old mobile AMD athlon xp, getting the following when I do 

chromium-browser -g
(gdb) start

Temporary breakpoint 1 at 0x806cbd8: file chrome/app/chrome_exe_main_gtk.cc, line 28.
Starting program: /usr/lib/chromium-browser/chromium-browser 
[Thread debugging using libthread_db enabled]

Program received signal SIGILL, Illegal instruction.
0x0859b6ae in tcmalloc::SizeMap::NumMoveSize (this=0xa1b2020, size=8) at third_party/tcmalloc/chromium/src/common.cc:59
59	third_party/tcmalloc/chromium/src/common.cc: No such file or directory.
	in third_party/tcmalloc/chromium/src/common.cc
(gdb) 


I did do the computer janitor thing, and the fix missing.

So that makes 3 of us so far who've posted with this problem, 2 with Karmic and me with Lucid, I'm seriously leaning towards a bad Chromium release, I'm using GChrome now and it's working great, may need to give another day to see if they cure illness.

---

### Post by ennui. on 2010-04-30
I have the same problem. I have the repos, tried purging, and reinstalling. I still see 'missing plug-in' when trying to watch streaming video.

What plug-in do i need to see enabled in about:plugins to watch, for example, a youtube video?

I did have streaming video for a bit in chromium before I installed mplayer. I have since uninstalled it but that hasn't seemed to help.

---

### Post by dkbiby on 2010-05-02
Not sure if this on topic or helps but I'm still on Hardy and my chromium browser stopped working after the daily build yesterday.  When I try to run chromium-browser from the command line I get a quick 'Illegal Instruction'  chromium-browser -g gives me; 

# Env:
#     LD_LIBRARY_PATH=/usr/lib/chromium-browser
#                PATH=/usr/lib/chromium-browser:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
#            GTK_PATH=
# CHROMIUM_USER_FLAGS=
#      CHROMIUM_FLAGS=
/usr/bin/gdb /usr/lib/chromium-browser/chromium-browser -x /tmp/chromiumargs.Lg8817
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb)

---

### Post by kc8hr on 2010-05-02
I am also on Hardy, and I get the identical output.

> **dkbiby said:**
> Not sure if this on topic or helps but I'm still on Hardy and my chromium browser stopped working after the daily build yesterday.  When I try to run chromium-browser from the command line I get a quick 'Illegal Instruction'  chromium-browser -g gives me; 

# Env:
#     LD_LIBRARY_PATH=/usr/lib/chromium-browser
#                PATH=/usr/lib/chromium-browser:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
#            GTK_PATH=
# CHROMIUM_USER_FLAGS=
#      CHROMIUM_FLAGS=
/usr/bin/gdb /usr/lib/chromium-browser/chromium-browser -x /tmp/chromiumargs.Lg8817
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb)

Shame, cuz it's a good, fast browser. Hope they fix it soon!

---

### Post by uRock on 2010-05-02
It would appear that you need to uninstall and remove all conf files for Chromium, then reinstall. don't forget to run autoremove before reinstalling.

---

### Post by jnmjr on 2010-05-02
> **kc8hr said:**
> I am also on Hardy, and I get the identical output.

Shame, cuz it's a good, fast browser. Hope they fix it soon!

> **uRock said:**
> It would appear that you need to uninstall and remove all conf files for Chromium, then reinstall. don't forget to run autoremove before reinstalling.

Something happened to Chromium, can't say what it may be, but it's across the board, it's now working in 10.04 but it's actually an exact copy of Chrome, it has lost some of the functions of Chromium, I too hope it gets fixed soon, I miss those functions, I don't see the purpose of renaming Chrome to Chromium just because Ubuntu is supporting it. 

Uninstall reinstall will not fix the problem it's some sort of bug.

---

### Post by uRock on 2010-05-02
> **jnmjr said:**
> Something happened to Chromium, can't say what it may be, but it's across the board, it's now working in 10.04 but it's actually an exact copy of Chrome, it has lost some of the functions of Chromium, I too hope it gets fixed soon, I miss those functions, I don't see the purpose of renaming Chrome to Chromium just because Ubuntu is supporting it. 

Uninstall reinstall will not fix the problem it's some sort of bug.

I did a clean install with no prior install of Chromium on 9.x releases. It is working fine on this system, which is why I say you may need to remove all instances of Chromium between uninstalling and reinstalling. There has to be a configuration file for the old version that is causing this problem.

---

### Post by Toost Inc. on 2010-05-02
The latest update (5.0.393.0~svn20100430r46027-0ubuntu1~ucd1) of Chromium from the PPA fixed the problem for me, complete with settings, which is weird since I DID purge it once... But all for the better anyway

---

### Post by ennui. on 2010-05-03
Could someone maybe let us know what/where some of these config files may be? Getting rid of the chromium files in ~/.confg didn't help the problem.

By the way, this is the error I get when trying to load a page with flash>

[7281:7281:18146767451:ERROR:webkit/glue/plugins/webplugin_delegate_impl_gtk.cc(124)] Not implemented reached in bool WebPluginDelegateImpl::WindowedCreatePlugin() windowed plugin but without xembed. See [http://code.google.com/p/chromium/issues/detail?id=38229](http://code.google.com/p/chromium/issues/detail?id=38229)


but that link is of no help.

---

### Post by jnmjr on 2010-05-03
> **ennui. said:**
> Could someone maybe let us know what/where some of these config files may be? Getting rid of the chromium files in ~/.confg didn't help the problem.

By the way, this is the error I get when trying to load a page with flash>

[7281:7281:18146767451:ERROR:webkit/glue/plugins/webplugin_delegate_impl_gtk.cc(124)] Not implemented reached in bool WebPluginDelegateImpl::WindowedCreatePlugin() windowed plugin but without xembed. See [http://code.google.com/p/chromium/issues/detail?id=38229](http://code.google.com/p/chromium/issues/detail?id=38229)


but that link is of no help.

The fact is at this time no one really knows what the problem is, I too removed all, purged, autoremoved, deleted .config file Chromium, have spent a ton of time looking for other "config files", as far as I can tell nothing else exists, I also ask ..If somebody out there knows of other buried files please list them....THX

---

### Post by kc8hr on 2010-05-03
I uninstalled the version from the repos, went to Google--http://code.google.com/intl/en/chromium/-- and downloaded the file directly and installed the .deb--and it worked!

---

### Post by jnmjr on 2010-05-03
> **kc8hr said:**
> I uninstalled the version from the repos, went to Google--http://code.google.com/intl/en/chromium/-- and downloaded the file directly and installed the .deb--and it worked!

Can you post what version you installed? THX

---

### Post by uRock on 2010-05-03
This one works great.

---

### Post by jnmjr on 2010-05-03
This one works great.[/QUOTE]

Try this one...[ATTACH]155362[/ATTACH]

---

### Post by kc8hr on 2010-05-04
> **jnmjr said:**
> Can you post what version you installed? THX

Certainly: 5.0.342.9 beta

Obtained from this link just yesterday (5/3/10): [http://www.google.com/chrome/eula.html?hl=en]("http://www.google.com/chrome/eula.html?hl=en")

---

### Post by uRock on 2010-05-04
That is not Chromium.

---

### Post by Ozymandias_117 on 2010-05-04
> **uRock said:**
> That is not Chromium.

Looks to me like he most likely has the daily PPA and you just have the one from Repos :P

---

### Post by uRock on 2010-05-04
> **Ozymandias_117 said:**
> Looks to me like he most likely has the daily PPA and you just have the one from Repos :P
His link went to Chrome's download page. Yep, I have the one from the repos or should I say had. I am currently reinstalling Karmic on my desktop.

---

### Post by kc8hr on 2010-05-04
> **uRock said:**
> That is not Chromium.

Whatever...It is the Google Chrome web browser, and it does work.

---

### Post by uRock on 2010-05-04
> **kc8hr said:**
> Whatever...It is the Google Chrome web browser, and it does work.
I have had too many problems with their PPA servers not connecting for updates. I am sure it works, but many people prefer Chromium for being open sourced.

---

### Post by jnmjr on 2010-05-04
> **uRock said:**
> That is not Chromium.

> **kc8hr said:**
> Whatever...It is the Google Chrome web browser, and it does work.

The point of this discussion was to try resolving the problem **Chromium**has working properly in Ubuntu, as uRock said Chrome is not Chromium, your whatever response means nothing we all know Chrome works fine in 10.04, those of us who prefer open source **Chromium** from the daily PPA's are the ones having problems, so, what's your point kc8hr?

---

### Post by jnmjr on 2010-05-04
Seems latest update has done the trick, Chromium is now working for me....THX all for your input):P.

---

### Post by ennui. on 2010-05-05
my chromium still thinks the flash plugin is 'missing'

---

