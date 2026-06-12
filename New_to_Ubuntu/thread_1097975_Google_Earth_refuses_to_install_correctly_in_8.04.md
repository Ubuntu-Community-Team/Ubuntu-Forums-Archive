---
title: "Google Earth refuses to install correctly in 8.04"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-16
Hello Ubunteros!

I've been trying to get Google Earth 4.3 to install using Synaptic Package Manager. It does install but where in the world is the world??? I mean the globe. It's gone, or missing, or simply hasn't loaded.

I've read all the advice on the forums and nothing has helped me to get it working.

Also, I'd like to know how I can clear everthing that has something to do with Google Earth. I've been trying .bin files and downloading from google and many other things and don't know if this mess is causieng me more trouble.

So those are my 2 hopes to accomplish.

1) Get Google Earth to work
2) delete all files and folders relating to google earth before next install attempt.

Is this possible? If so how?

---

### Post by Dougie187 on 2009-03-16
If you have installed it from synaptic, try opening a terminal and typing
```
googleearth
```

You can also look in /opt/google-earth to see if there are files there, as that is where I think it typically installs to.

It might give you an error message like this
```
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```

If you get this message, then you have to type the following in
```
cd /opt/google-earth
sudo mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.old
sudo ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8
```

Then you should be able to try googleearth again and see if it runs.

Now, if you don't have googleearth, or if it tells you command not found, then it is most likely not installed from synaptic. So you can either install it in googleearth, or you can install it from the .bin file. I would recommend the synaptic route, unless you need google 5.0. If you need google 5.0 download the binary file, and in a terminal cd into the directory that contains it.

After you get there, you have to chmod that file so you can install it. I believe it should be called GoogleEarthLinux.bin, so after you cd to the directory type the following to install it.

```
chmod 755 GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

And that should install the program. After it installs, you might see the error message mentioned above, and in that case do the same fix that I described above.

To remove the previous google earth installation, you can type
```
sudo apt-get autoremove googleearth
```

and that should clear off everything.

---

### Post by suomalainen on 2009-03-16
Dougie187!,

Thanks for taking the time to write all this. I'm ok with GE ver. 4.3.

I cleaned up everything first then went to Synaptic Package Manager {SPM} and installed GE 4.2... But it wouldn't load. It only crashed. I uninstalled it via SPM and then installled GE 4.3. 4.3 is installed but I'm only seeing black shy. Also, during the install process it didn't get listed under Applications--> Internet! I wonder what happened????

What is the black screen all about????? Any ideas?

Thanks again!

---

### Post by Dougie187 on 2009-03-16
Did you try running it from the command line? If you do that it should give you some useful information. Also, you might try checking out your syslog, or dmesg for some more useful information.

---

### Post by suomalainen on 2009-03-16
Well the issue now is that I just sit staring at a black screen. The globe is missing.

---

### Post by Therion on 2009-03-16
Try this:
Step 1:  ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Step 2:  ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get install googleearth-4.3
```


Joy?

---

### Post by suomalainen on 2009-03-16
Therion,

I used SPM to uninstall the previous version of GE 4.3 that I had installed.

Then I proceeded forward by following the 2 steps you offered.

Under Applications --> Internet Google Earth is not listed. So I opened up Terminal and typed GOOGLEEARTH and the program launched.

However, I still  have the same problem, The globe is missing. I'm just looking at black screen. BUT HERES THE REAL STRANGE PART... If I click on "View" and remove the "checK" mark next to "SideBar" the The globe appears. When I "Check/ticK" the sidebar option again the globe remains but looks like this. See attached pic.

I also received this crash/bug report


john@john-desktop:~$ googleearth
googleearth-bin: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
Google Earth has caught signal 6.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin [0x804f403]
  /usr/lib/googleearth/googleearth-bin [0x804f916]
  [0xb7f0a420]
  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb70b9a01]
  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb70b110e]
  /usr/lib/dri/unichrome_dri.so(_mesa_reference_renderbuffer+0x14e) [0xae57e32e]
  /usr/lib/dri/unichrome_dri.so(_mesa_free_framebuffer_data+0x67) [0xae559537]
  /usr/lib/dri/unichrome_dri.so(_mesa_destroy_framebuffer+0x26) [0xae559626]
  /usr/lib/dri/unichrome_dri.so(_mesa_unreference_framebuffer+0x6b) [0xae5593ab]
  /usr/lib/dri/unichrome_dri.so [0xae515e40]
  /usr/lib/dri/unichrome_dri.so [0xae50b6f0]
  /usr/lib/dri/unichrome_dri.so [0xae50b0be]
  /usr/lib/dri/unichrome_dri.so [0xae50b2f5]
  /usr/lib/libGL.so.1 [0xb6644113]
  /usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext22internalDestroyContextEv+0x41) [0xb45fbfa1]
  /usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext12userDestructEv+0x7b) [0xb4634dbb]
  /usr/lib/googleearth/libIGCore.so(_ZNK3Gap4Core8igObject15internalReleaseEv+0x8b) [0xb699244b]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContextD2Ev+0xff) [0xb39d0fdf]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17VisualContextUnixD0Ev+0x2d) [0xb3c2907d]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImplD0Ev+0x1cf) [0xb3b7b51f]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl15DeleteSingletonEv+0x2e) [0xb3b58e2e]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7APIImpl19deleteRenderContextEv+0x17) [0xb3ad1757]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7APIImpl8shutdownEv+0x36) [0xb3ad18f6]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7APIImplD0Ev+0x2d) [0xb3ad947d]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll7APIImpl15DeleteSingletonEv+0x2b) [0xb3ad159b]
  /usr/lib/googleearth/libevll.so(releaseApi+0x17) [0xb3ad1977]
  /usr/lib/googleearth/libapiloader.so(_ZN5earth4evll9ApiLoader10releaseApiEv+0x19) [0xb69095f9]
  /usr/lib/googleearth/libmoduleframework.so(_ZN5earth6module13ModuleManagerD0Ev+0x8a) [0xb67c147a]
  /usr/lib/googleearth/libmoduleframework.so(_ZN5earth6module13ModuleContextD0Ev+0x31) [0xb67c0cd1]
  /usr/lib/googleearth/libmoduleframework.so(_ZN5earth6module13ModuleContext15DeleteSingletonEv+0x26) [0xb67bec86]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11ApplicationD1Ev+0x24c) [0xb726eb5c]
  /usr/lib/googleearth/googleearth-bin(main+0x2c4) [0x8050bf4]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70a3450]
  /usr/lib/googleearth/googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/john/.googleearth/crashlogs/crashlog-FD6E37E5.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by mvalviar on 2009-03-16
Have you tried running google earth with "sudo googleearth?". Try it, and if it runs properly then it could be permission issues. If it is run this code on you home directory.

```
sudo chown -R $USER:$USER .config/
```

---

### Post by suomalainen on 2009-03-16
Listen Folks , I've installed Google Earth on plenty of Ubuntu machines and this is the first time I have simply run up against a brick wall.... It's like the forces don't want me to have it or something...... :(

Here's the type of machine I got:

HP Pavilion a500n desktop PC
Product number DW230A
AMD Athlon XP (B) 2800+ 2.08 GHz
Advanced 333 MHz front side bus
Socket A
512 MB RAM
ASUS A7V8Z-LA Motherboard

Dual boot machine

50% allocated to Windows XP
50% to Linux Ubuntu 8.04LTS

So what's the deal that Google Earth 4.3, 4.3 & 5.0 just will not install?

Any info welcomed! Serious replies please......

---

### Post by suomalainen on 2009-03-17
Ubunteros,

I just did a fresh install of 8.04LTS. Do I need to install any specific drivers for Google Earth to install and function properly?

I have no clue why GE doesn't want to load properly. As noted above:

1) First an empty black screen appearswith no globe.
2) Upon fidelling with "side part" globe appears but is missing some of it's side.

And help appreciated.

---

### Post by gandaran on 2009-03-17
> So what's the deal that Google Earth 4.3, 4.3 & 5.0 just will not install?
1º you video card drivers, if you have a nvida card try installing the latest driver.
2º are you running compiz/desktop effects? turn them off and try again.

---

### Post by barbedsaber on 2009-03-17
google have said that some people experience issues with google earth in linux (globe not showing up) it is a permissions problem, and running
```
sudo googleearth
```
is a quick fix.
I think they are working on the problem, but this has been happening to a lot of people for ages, I am loosing hope.
anyway, hope that cleared it up for you.

---

### Post by suomalainen on 2009-03-17
gandaran,

This is a fresh install of 8.04. The first piece of software I'm installing is Google Earth. Thus, I haven't dowmloaded anything else except this one program. ALSO, I have adjusted any settings.

The graphics card is integrated into the motherboard. I don't have a card.

ANy ideas why GE don't launch properly?

---

### Post by gandaran on 2009-03-17
> The graphics card is integrated into the motherboard. I don't have a card.
integrated or not, is it nvidia, ati, intel or something else? it must be a video drivers problem but I have read some forum posts here where you can fix these type of problems by editing some system file, if I find one I will post it.

---

### Post by suomalainen on 2009-03-17
gandaran,


I posted these specs on page 1 of this thread:

HP Pavilion a500n desktop PC
Product number DW230A
AMD Athlon XP (B) 2800+ 2.08 GHz
Advanced 333 MHz front side bus
Socket A
512 MB RAM
ASUS A7V8Z-LA Motherboard

I tried looking up the chipset and info on the integrated video card for the motheboard and found nothing.

Are their offical online sources I may not know about that can provide the info I need?

---

### Post by gandaran on 2009-03-17
> **suomalainen said:**
> gandaran,


I posted these specs on page 1 of this thread:

HP Pavilion a500n desktop PC
Product number DW230A
AMD Athlon XP (B) 2800+ 2.08 GHz
Advanced 333 MHz front side bus
Socket A
512 MB RAM
ASUS A7V8Z-LA Motherboard

I tried looking up the chipset and info on the integrated video card for the motheboard and found nothing.

Are their offical online sources I may not know about that can provide the info I need?
install sysinfo, then go to applications»system tools»sysinfo, it will show every bit of hardware information.
check system»hardware drivers, does it show any drivers install option?

---

### Post by suomalainen on 2009-03-17
gandaran,

Does this help?

GRAPHIC CARD
	VGA controller
		VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA controller])
		Subsystem: ASUSTeK Computer Inc. Unknown device 8118

---

### Post by gandaran on 2009-03-17
> **suomalainen said:**
> gandaran,

Does this help?

GRAPHIC CARD
	VGA controller
		VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA controller])
		Subsystem: ASUSTeK Computer Inc. Unknown device 8118
no, it doesn't help! I didn't even know VIA make GPU's, the driver is surely your problem, if you can't fix it by editing some file then buy a nvidia pci card.

---

### Post by suomalainen on 2009-03-17
I'm sorry how did we deem this issue a driver problem exactly? Is this a hunch or fact?

---

### Post by gandaran on 2009-03-17
> **suomalainen said:**
> I'm sorry how did we deem this issue a driver problem exactly? Is this a hunch or fact?
you are right, I don't know, its just a hunch, on this computer I'm writing from I can't even run googleearth due to my sis integrated GPU, this sis card driver is only 2D, linux googleearth works only with 3D, wont even open.

---

### Post by t0p on 2009-03-17
> **suomalainen said:**
> I'm sorry how did we deem this issue a driver problem exactly? Is this a hunch or fact?

I've just read through this thread and I also don't know how this became a drivers issue. I noticed a few folk suggested starting GE with the command ```
sudo googleearth
``` and I don't think the OP has said yet if he has tried it. So tell us, OP!

---

### Post by suomalainen on 2009-03-17
Do you call me OP like that little boy in Andy Griffith show? Or what does this word mean?

I used sudo googleearth and it didn't work. If I used it as noted earlier and it were to have worked I would have marked thread as solved and said Thank You to everyone.

But problem isn't solved.

I think the pic I attached speaks 1000 words cause partial globe appears but the rotation tools are missing and it appears that screen the globe appears in cuts part of globe away. Picture says it all.

---

### Post by suomalainen on 2009-03-17
Do you guys think I should to a re-install of Ubuntu?

---

### Post by gandaran on 2009-03-17
why not! but try ubuntu 8.10, maybe it has better video card support!

---

### Post by suomalainen on 2009-03-17
No Thank You! 8.04 IS THE BEST!

Like they say if it ain't broke don't fix it!

Anyone else have any ides what shuld/could be  done?

---

### Post by gandaran on 2009-03-17
> **suomalainen said:**
> No Thank You! 8.04 IS THE BEST!

Like they say if it ain't broke don't fix it!

Anyone else have any ides what shuld/could be  done?
why is it the best? I have used ubuntu since 7.04, ubuntu 8.04 was the only one that give me problems, now and then it got broken with updates.

---

### Post by suomalainen on 2009-03-17
That's only your opinion. I don't have to change to something I already like! And that works!!!! Anyway if it isn't LTS approved your running risks!

---

### Post by gandaran on 2009-03-17
> Anyway if it isn't LTS approved your running risks!
???

---

### Post by suomalainen on 2009-03-17
Can we please reserve this space for those individuals that would like to help me please! Thanks for your cooperation.

---

### Post by augustos on 2009-03-17
I have the same problem with Kubuntu 8.10 Intrepid.Google earth 4.3 starts but it`s impossible to work with the globe and google eart 5 not even start. I'm still waiting for a solution too.

---

### Post by Dougie187 on 2009-03-17
Have you by any chance tried clearing out the ~/.googleearth directory?

I'm not sure if that would help any, but it's worth a shot.

EDIT:
Also, which version of google earth are you using, and which problem do you get with which version?
So far I know you have tried 4.2 4.3 and 5, but the only error I have read is that you get a blank screen with no globe on it. Which version is it that gave you this, and what do the other versions do?

And for future reference, when looking for your video card information you can use lspci from command line, and you can use lshw as well. lspci is only really useful if you know what to grep for, otherwise you have to dig, but you can try
```
lshw -c video
``` and that should give you useful information about your video card.

---

### Post by gandaran on 2009-03-17
suomalainen
I have found something on this [page]("http://www.vivaolinux.com.br/topico/Ubuntu-e-Kubuntu/Google-Earth-no-Kubuntu-8.04") (it's in Portuguese) from someone that has the same error output, he said the fix is to substitute the libGL.so.1 in /usr/lib/googleearth to a newer libGL.so.1.2, you'll have to get this file, hope this helps.

---

### Post by Dougie187 on 2009-03-17
> **gandaran said:**
> suomalainen
I have found something on this [page]("http://www.vivaolinux.com.br/topico/Ubuntu-e-Kubuntu/Google-Earth-no-Kubuntu-8.04") (it's in Portuguese) from someone that has exactly the same error output, he said the fix is to substitute the libGL.so.1 in /usr/lib/googleearth to a newer libGL.so.1.2, you'll have to get this file, hope this helps.

He could probably just link to the one in /usr/lib which would depend on his graphics card.

---

### Post by suomalainen on 2009-03-17
> **Dougie187 said:**
> EDIT:Also, which version of google earth are you using, and which problem do you get with which version? So far I know you have tried 4.2 4.3 and 5, but the only error I have read is that you get a blank screen with no globe on it. Which version is it that gave you this, and what do the other versions do?.

As hard as it may be to believe they all give the exact same result.
 But from here forward, I'll stick with 4.3 and get it working!!!

---

### Post by suomalainen on 2009-03-17
Here is the info I got back using the command  Dougie187 provided but I don't see anything about video in it. Am I missing something.???




lshw -c video
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by Dougie187 on 2009-03-17
> **suomalainen said:**
> As hard as it may be to believe they all give the exact same result.
 But from here forward, I'll stick with 4.3 and get it working!!!

Heh, well good luck. Have you tried any of the things listed in the last couple posts yet?

Sorry, I messed up the flag, it should be either one of the following
```
lshw -C video
lshw -class video
```

Did you try clearing out your googleearth directory?

---

### Post by suomalainen on 2009-03-17
OK here is the output I received based on the new code:

lshw -class video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0

Does this mean anything?

I can't move forward on the Portugal claim cause it's in different language. This is one I don't speak. I need step by step so I don't goof up.  Sorry, but thank you for the advice! It's most appreciated!!!!

---

### Post by Dougie187 on 2009-03-17
> **suomalainen said:**
> 
lshw -class video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0


Well, it doesn't really tell me anything, because I found other people who have this same graphics card and say it is unclaimed as well. Just for your future reference though, you have an Intel 82Q963/Q965 Integrated Graphics Controller. 

Try to clear out your .googleearth directory, and I will work on getting some step by step instructions for you from the foreign site.

Also, could you post the results of this command.
```
ls /opt/google-earth
```

---

### Post by gandaran on 2009-03-17
suomalainen

the instructions are simple, just substitute libGL.so.1 to libGL.so.1.2 in /usr/lib/googleearth.
check if you have this libGL.so.1.2 in /usr/lib ( I have both libGL.so.1 and libGL.so.1.2 in ubuntu 8.10) apparently libGL.so.1.2 fixes googleearth issues with ati video cards, hope it'll work for your intel card too.
google libGL.so.1.2 to find out more
and see [this]("http://bbs.archlinux.org/viewtopic.php?id=36911")  theres a fix here too.

---

### Post by Dougie187 on 2009-03-17
The reason I asked for that ls was because in my googleearth directory, there isn't a libGL file. there is however libGLU, so i don't know if he needs glut, or gl...

Also, the path for my installed google-earth is /opt/google-earth. Again I am running version 5.0 though.

---

### Post by augustos on 2009-03-18
I sort out the problem turning desktop effects off on kubuntu intrepid and google earth 4.3 Try this if you dont do it before.

---

### Post by hs3l on 2009-03-20
Hi I would like to borrow this thread to explain my problems.
Hope I'm not budging in as I'm totally new to Linux.

I am also encountering some problems with Google Earth after installing it as advised in post #6 of this thread by Therion.

The installation seems to go fine.Was able to launch the program but the display looked a bit weird.

I've taken a screenshot of it.The texture looks grainy/distorted and after a few seconds running, my whole screen went blackout. 

The details of my graphics card and hardware:
Intel Core 2 Duo 
Intel DG965RY mobo
Integrated Intel X3000 GMA 
Integrated Intel HD Sound

When I launch System--> Administration --> Hardware Drivers, the list is blank.I hope everything looks fine. From what I've read after doing some search, it says Google Earth needs 3D acceleration turned on. 

Can someone guide me on this?

Thanks.

[IMG]http://img18.imageshack.us/img18/8400/googleearth1.png[/IMG]

---

### Post by augustos on 2009-03-20
Did you try turning desktop effects off?

---

### Post by Licurgo on 2009-03-20
Hey boys:
I'm going to lend this post and ask for help.
My story is a little bit different, Googleearth starts and then suddendly dissapears, in the terminal says:

Warning: Unable to create prefs directory '/root/.googleearth'. El fichero ya existe.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

Any help, please
;)

---

### Post by Dougie187 on 2009-03-21
> **Licurgo said:**
> Hey boys:
I'm going to lend this post and ask for help.
My story is a little bit different, Googleearth starts and then suddendly dissapears, in the terminal says:

Warning: Unable to create prefs directory '/root/.googleearth'. El fichero ya existe.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

Any help, please
;)

You should read the whole post before jacking it. I posted an answer to this question in my first post.

Also, to everyone else who is trying to thread jack (or borrow the thread) you should probably post your questions in your own thread, as you won't get much attention, if any here.

---

