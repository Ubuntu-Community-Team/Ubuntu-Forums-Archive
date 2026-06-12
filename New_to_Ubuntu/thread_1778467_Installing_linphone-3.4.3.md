---
title: "Installing linphone-3.4.3"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-06-09
I'm trying to install linphone-3.4.3 and I've downloaded linphone-3.4.3.tar.gz and extracted its contents to my home/john directory,  and found an INSTALL file there which tells me to start by typing ./configure.   
This runs and does a lot of checking but comes up with 
> configure: error: Your intltool is too old.  You need intltool 0.40 or later.
OK, so now I look in Synaptic Manager and find
> intltool      0.41.0-Oubuntu1  Utility scripts for internationalising XML
Since it looks as if my intltool is actually up-to-date, what should I do now to get configure to recognise this and allow me to proceed?
I notice that linphone-3.4.3.tar.gz has unpacked three intltool files:

/home/john/linphone-3.4.3/intltool-extract.in   0 bytes
/home/john/linphone-3.4.3/intltool-merge.in     0 bytes
/home/john/linphone-3.4.3/intltool-update.in    0 bytes

I'm confused because I don't know where I should look for my system's intltool files, nor can I work out why the above three intltoolfiles are there or what they are supposed to do.

Can anyone point me in the right direction, please?

---

### Post by jtarin on 2011-06-09
> **Sleepy-zz-John said:**
> 
OK, so now I look in Synaptic Manager and find
```
intltool 0.41.0-Oubuntu1 Utility scripts for internationalising XML 
```

Since it looks as if my intltool is actually up-to-date, what should I do now to get configure to recognise this and allow me to proceed?Is it marked as actually being installed?

---

### Post by Sleepy-zz-John on 2011-06-09
> **jtarin said:**
> Is it marked as actually being installed?
Ah,  no,  it wasn't !  :redface:
Thanks!    That's fixed that problem now   :D

But now I'm getting another problem:

> configure: error: Package requirements (gtk+-2.0 >= 2.4.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGTK_CFLAGS
and LIBGTK_LIBS to avoid the need to call pkg-config. 

So I've tried entering:
"pkg-config LIBGTK_CFLAGS"    and "pkg-config LIBGTK_LIBS"
without effect.   Still getting the same "Package requirements (gtk+-2.0 >= 2.4.0 gthread-2.0) were not met". 

I'm wondering if there's an easier more friendly way of dealing with these dependency issues that are arising 'cos I'm finding myself a bit lost with the error messages.   

I previously installed linphone v 3.1.2,  which is all that's available in the Ubuntu Software Centre,  without running into any dependency issue troubles.  My troubles now seem to be arising as a result of me using the later downloaded linphone-3.4.3.tar.gz version.

Any ideas?

---

### Post by jtarin on 2011-06-09
This is why Software in the Ubuntu Software Center is recommended. All dependencies are met. If you go outside that then you will find yourself in this situation. It's not impossible but you need to know what your doing. After a time you will. Use Google when you get these error messages.....they are there for a reason to help you. In Synaptic search for **_libglib2.0-dev_** and install then run your routine again. There could be other dependencies or not. Post back.

---

### Post by Sleepy-zz-John on 2011-06-09
> **jtarin said:**
> This is why Software in the Ubuntu Software Center is recommended. All dependencies are met. If you go outside that then you will find yourself in this situation. It's not impossible but you need to know what your doing. 
OK, thanks.   That explains a lot.
> After a time you will. 
Hope you're right!  Your supportive words certainly help, anyway!
>  Use Google when you get these error messages.....they are there for a reason to help you.
Good advice
>  In Synaptic search for **_libglib2.0-dev_** and install then run your routine again. 
Right.   Done that and it's fixed my gthread-2.0 error but still left me with a "No package 'gtk+-2.0' found" one.   However I then followed your above advice and discovered I needed libgtk2.0-dev to get that,  which I was able to do with an apt-get install.  So that's two of them fixed so far.  
Must say I'm surprised at the large size of the packages.  Looks like a gross overkill for little old Linphone, and I can hear a perfectionist voice inside me saying I ought to think about tidying up and removing the unnecessaries some time in the future.  
> There could be other dependencies or not. Post back.
Yes,  another one then came up:
"configure: error: Could not find osip2 headers !"
OK,  so to fix that I added libexosip2-dev and libosip2-dev and that appears to have been successful.   
Again, though,  the package sizes feel like they're an overkill.
The next error I'm getting now is "No package 'speex' found".   

I'm going to take a break at this point,  since I feel all these missing dependencies are making my Linphone 3.4.3 installation quite heavy going,  especially considering I previously had all the dependencies for Linphone 3.1.2 in place and working. 

Any further general comments,   bearing in mind that thanks to the good earlier advice here,  I now seem to be managing to find particular solutions by myself ?

---

### Post by jtarin on 2011-06-09
Good you've found your way. :p This is exactly how I started almost 13 years ago with Linux.....Google was my manual. Now it's even a better one. As to your feeling top heavy with installed apps that is normal. I normally uninstall through Synaptic those I don't want or need. I also keep a lot of data on an external hard drive. My Ubuntu system is at about at 50% on a 50GB partition. Most of these apps your installing are small and most are only for compiling software, which has already been done in the Software Center. I very rarely use the thing. :p Here's a[ link]("http://packages.ubuntu.com/search?keywords=speex") for some speex files all packaged up for your version of Ubuntu. Here is also a [link]("http://forums.techarena.in/guides-tutorials/1153979.htm") on "alien" a package converter you may or may not want to use some time. Read the caveats and [manpage]("http://www.debianadmin.com/manpages/alienmanpage.txt").Oh you might uninstall your present Linphone before installing the new. That way you won't get too bloated.

---

### Post by Sleepy-zz-John on 2011-06-10
Thanks for comments jtarin.  Thought I was doing quite well yesterday,  but now find I'm stuck again today! :(  I've now downloaded 'speex' package v 1.2~rc1.1 (karmic) and synaptic is now showing this list of installed files:

/.
/usr
/usr/bin
/usr/bin/speexenc
/usr/bin/speexdec
/usr/share
/usr/share/doc
/usr/share/doc/speex
/usr/share/doc/speex/AUTHORS
/usr/share/doc/speex/README
/usr/share/doc/speex/TODO
/usr/share/doc/speex/copyright
/usr/share/doc/speex/NEWS.gz
/usr/share/doc/speex/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/speexdec.1.gz
/usr/share/man/man1/speexenc.1.gz

But configure for linphone is still not recognising it:

> checking for SPEEX... no
configure: error: Package requirements (speex >= 1.1.6) were not met:

No package 'speex' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SPEEX_CFLAGS
and SPEEX_LIBS to avoid the need to call pkg-config.

Now I can see from Google and forum searches that there are lots of people getting similar warnings from their ./configure commands about a whole variety of missing packages,  not just for linphone and speex, but for a whole range of other installations they're all attempting.  For one reason or another "configure" isn't finding stuff that's already installed, and we all keep getting these two paragraphs "Consider adjusting the PKG_CONFIG_PATH environment variable...."  and "Alternatively,you may set the environment variables...."  which on the whole it seems people don't really understand and can't follow any more than I can :confused:.

So now my questions are:  
1)  Where can we find this "environment variable"  and how exactly can it be adjusted with pkg-config?   

2)  How in general can we set environment variables  like SPEEX_CFLAGS
and SPEEX_LIBS or whatever?   How would we know how to locate the appropriate directory and file?

I'm hoping that a general descriptive answer rather than one that's limited to my current linphone - speex issue might help quite a lot of other folk besides myself who are confused and lost on these two paragraphs.

BTW,  curious to know if your Lat and Long coordinates are N and E respectively??

---

### Post by jtarin on 2011-06-10
Look at your script that is used for configuring your application (configure). It is the one that is executed when you enter the command ./configure.
Open it in a text editor and you can see the PATHS it is looking to find the installed software...in this case speex. Adjust it to the actual location then try again. Make a backup before you edit it. "configure.orig"

---

### Post by jtarin on 2011-06-10
> BTW, curious to know if your Lat and Long coordinates are N and E respectively??Yes

(I edited the post above.)

---

### Post by jtarin on 2011-06-10
> I'm hoping that a general descriptive answer rather than one that's limited to my current linphone - speex issue might help quite a lot of other folk besides myself who are confused and lost on these two paragraphs.They call them variables for a reason. You build and install a package and it is a non-standard package to that version of Linux it has dependencies that it must meet.It must look for those dependencies in expected locations to build. If it cannot find them....it doesn't build. In essence you application is looking for speex and speex is where it should be according to Debian packaging, but.......you have decided to build a package that was not packaged for Debian and it is looking in non-Debian locations for speex and cannot find it. You have to help it find speex so it know the dependencies are met and it can continue its build.Any questions? You can post a copy of your configure script and I'll look at it.

---

### Post by Sleepy-zz-John on 2011-06-10
> **jtarin said:**
> ........Any questions? You can post a copy of your configure script and I'll look at it.

Thanks.  Your great support much appreciated,  and it seems I'm still in need of it.

There are several configure script candidate files, some large, some small, as per list below, and I'm not sure which I should post.  I've had a cursory look through them to see if I could recognise code that includes both speex and a file location to search in, but this was inconclusive.   speex appears extensively in the first four on the list,  and not at all in the last two.   I'm not even sure whether that really rules out the last two as candidates because they might still contain generic file location search instructions.  The string /usr certainly appears extensively throughout. 

/home/john/linphone-3.4.3/mediastreamer2/configure.ac  19.6KB
/home/john/linphone-3.4.3/mediastreamer2/configure  638.4KB
/home/john/linphone-3.4.3/configure.ac   15.9KB
/home/john/linphone-3.4.3/configure  577.1KB
/home/john/linphone-3.4.3/oRTP/configure.ac   10.6KB
/home/john/linphone-3.4.3/oRTP/configure  417.6KB

I fear it would be a bit too heavy to post all these configure files on the forum.   Would it make more sense to suggest downloading the original "linphone-3.4.3.tar.gz?     Alternatively I'm open to suggestions about what I should be specifically be looking for in those six configure files.  

Many thanks again

(19.49N 99.45E)

---

### Post by jtarin on 2011-06-10
This should be the one:/home/john/linphone-3.4.3/configure 577.1KB
It will mention the PATH= (to different files it must be able to locate totell the program when it is building where it can find these things after installation.)Example:I move a houseful of furniture for you and you have not labeled any of the containers as to which room they should be in. I am used to putting things where "I think" they should go and my best guess turns out not to be where you want them.....so you have to label the containers and give me a map of the house.Because I think all houses are alike with the rooms in the same place. Catch my drift?

---

### Post by Sleepy-zz-John on 2011-06-11
Yep, I get that general drift OK,  but now I'm afraid it's the detail that's flooring me  :(

If I understand correctly,  the file "speex.pc" should appear in /usr/lib/pkgconfig in order for pkg-config to be able to find where all the necessary speex files are located.    But there's no sign of "speex.pc" there or anywhere else as far as I can see.

Neither does a search for a speex directory come up with anything other than usr/share/doc/speex which only contains a few not-so-useful documentary files. 

I've tried removing and re-installing speex in Synaptic but this still doesn't seem to yield anything I can use

/.
/usr
/usr/bin
/usr/bin/speexenc
/usr/bin/speexdec
/usr/share
/usr/share/doc
/usr/share/doc/speex
/usr/share/doc/speex/AUTHORS
/usr/share/doc/speex/README
/usr/share/doc/speex/TODO
/usr/share/doc/speex/copyright
/usr/share/doc/speex/NEWS.gz
/usr/share/doc/speex/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/speexdec.1.gz
/usr/share/man/man1/speexenc.1.gz

I also have the idea I could bypass pkg-config and use the following commands instead:

./configure --SPEEX_CFLAGS=XXXXXXXX
   and
./configure --SPEEX_LIBS=YYYYYYY

But I still don't know what to enter for XXXXXXXX or YYYYYYY.

I'd be happy to post my 577.1KB configure file here as suggested earlier if you still think it would help,  but my problem right now seems to be centred more on finding where my relevant speex files have ended up. 

Thanks again jtarin for your patient replies  :)

---

### Post by jtarin on 2011-06-11
> **Sleepy-zz-John said:**
> 
If I understand correctly,  the file "speex.pc" should appear in /usr/lib/pkgconfig in order for pkg-config to be able to find where all the necessary speex files are located.    But there's no sign of "speex.pc" there or anywhere else as far as I can see.

Neither does a search for a speex directory come up with anything other than usr/share/doc/speex which only contains a few not-so-useful documentary files.

Install libspeex-dev it can be found in Synaptic.

---

### Post by Sleepy-zz-John on 2011-06-12
> Install libspeex-dev it can be found in Synaptic. 

Yes, good,  that worked OK.   :)

I then went on to find and fix several more errors by adding -dev files.  but eventually came unstuck again in configure with:

```
checking X11/extensions/Xv.h usability... no
checking X11/extensions/Xv.h presence... no
checking for X11/extensions/Xv.h... no
checking for X11/extensions/Xvlib.h... no
checking for XvCreateImage in -lXv... no
configure: error: No video output API found. Install either X11+Xv headers or SDL library.
configure: error: ./configure failed for mediastreamer2
```

I found but couldn't download X11+Xv files,  so I thought I'd try 

libsdl-image1.2-dev  [development files for SDL 1.2 image loading library]

but that was calling for 16 files totalling 25MB to be added, and I felt I was getting myself into too deep waters since I wasn't really looking for video facilities in the first place.   

So I tried abandoning that error and proceeded to try "make" command.
make ran but mostly output  "nothing to be done" reports.   However it finished with a couple of errors:

```
make  all-recursive
make[1]: Entering directory `/home/john/linphone-3.4.3'
Making all in build
make[2]: Entering directory `/home/john/linphone-3.4.3/build'
Making all in macos
make[3]: Entering directory `/home/john/linphone-3.4.3/build/macos'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/john/linphone-3.4.3/build/macos'
make[3]: Entering directory `/home/john/linphone-3.4.3/build'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/john/linphone-3.4.3/build'
make[2]: Leaving directory `/home/john/linphone-3.4.3/build'
Making all in m4
make[2]: Entering directory `/home/john/linphone-3.4.3/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/linphone-3.4.3/m4'
Making all in pixmaps
make[2]: Entering directory `/home/john/linphone-3.4.3/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/linphone-3.4.3/pixmaps'
Making all in po
make[2]: Entering directory `/home/john/linphone-3.4.3/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/linphone-3.4.3/po'
Making all in oRTP
make[2]: Entering directory `/home/john/linphone-3.4.3/oRTP'
make[2]: *** No rule to make target `all'. Stop.
make[2]: Leaving directory `/home/john/linphone-3.4.3/oRTP'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/linphone-3.4.3'
make: *** [all] Error 2

``` 

Must say despite all your great help I'm feeling I've unwittingly bitten off rather more than I can chew with this linphone 3.4.3 installation,  and wondering if I should abandon it after all.   Of course it's hard to guess how many more problems still lie ahead with it.  If I thought I'd already overcome > 80% then of course it would be worth persevering for the last stretch. 

As my mentor and the one who is probably going to end up digging me out of more holes,   please give me your honest opinion:   Press on?   or Abandon?

---

### Post by jtarin on 2011-06-12
Your gonna S**T.....look what I found......[here]("http://www.google.com/search?client=ubuntu&channel=fs&q=linphone-3.4.3&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&pq=linphone-3.4.3&xhr=t&q=linphone-3.4.3+.deb&cp=15&pf=p&sclient=psy&client=ubuntu&hs=FHN&channel=fs&source=hp&aq=f&aqi=&aql=&oq=linphone-3.4.3+.deb&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=7ff7d408b5d36764&biw=1440&bih=731")

---

### Post by VOT Productions on 2011-06-12
Even better... do **sudo apt-get install linphone** in a terminal.

---

### Post by jtarin on 2011-06-12
> **VOT Productions said:**
> Even better... do **sudo apt-get install linphone** in a terminal.
I think your missing the point. :p That happens when you come late to a thread, but thanks for the input.

---

### Post by Sleepy-zz-John on 2011-06-13
> **jtarin said:**
> Your gonna S**T.....look what I found......[here]("http://www.google.com/search?client=ubuntu&channel=fs&q=linphone-3.4.3&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&pq=linphone-3.4.3&xhr=t&q=linphone-3.4.3+.deb&cp=15&pf=p&sclient=psy&client=ubuntu&hs=FHN&channel=fs&source=hp&aq=f&aqi=&aql=&oq=linphone-3.4.3+.deb&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=7ff7d408b5d36764&biw=1440&bih=731")

Wow!   Yes!   Having looked at all that,  I've now deleted my meagre installation attempts and am going to try and start from scratch with felix.lechner's linphone - 3.4.3-1~lucid~ppa1.

First steps seems to be to install  ppa:felix.lechner/linphone-ppa and do an apt-get update according to Step 3 in "Read about installing" on [https://launchpad.net/~felix.lechner/+archive/linphone-ppa](https://launchpad.net/~felix.lechner/+archive/linphone-ppa).

Current status is that my apt-get update finishes with:

```
W: Failed to fetch http://ppa.launchpad.net/felix.lechner/linphone-ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Not sure how significant this update failure is,  so I've tried e-mailing direct to felix.lechner to ask his advice. Will keep u advised.

Many thanks.

---

### Post by Irihapeti on 2011-06-13
The PPA problem is because Karmic Koala has reached the end of its life. See [http://ubuntuforums.org/showthread.php?t=1768343](http://ubuntuforums.org/showthread.php?t=1768343)

To use the PPA, you'd need to install a later version of Ubuntu.

---

### Post by Sleepy-zz-John on 2011-06-13
> **jtarin said:**
> 
[QUOTE=VOT Productions;]
Even better... do sudo apt-get install linphone in a terminal.
I think your missing the point. :p That happens when you come late to a thread, but thanks for the input.[/QUOTE]
Yes,  I think jtarin is right.  We already established earlier in this thread that linphone v 3.4.3 is not available in .deb form, hence all the struggles with dependencies.

---

### Post by jtarin on 2011-06-13
Seriously at this point updating to LTS 10.04....at least will save you some headaches. Just back up your home folder off disk. When Maverick is at end of life and things look bleak.....I'll probably switch back to Slackware.

---

### Post by Sleepy-zz-John on 2011-06-13
> **Irihapeti said:**
> The PPA problem is because Karmic Koala has reached the end of its life. See [http://ubuntuforums.org/showthread.php?t=1768343](http://ubuntuforums.org/showthread.php?t=1768343)

To use the PPA, you'd need to install a later version of Ubuntu.
Hmmm... Thanks for that.    Yes, I was aware support for Karmic ceased but was still encouraged because I feel sure I saw something on felix.lechner's ppa pages only yesterday indicating options for earlier versions still being available.  Huh!  Must have disappeared overnight :o 

OK,  although I'm not quite ready to do it yet, I was planning to upgrade anyway, and do have a burnt Natty .iso in readiness,  so looks like I'd better postpone this linphone ppa install until I'm up on Natty.  

Meanwhile thanks again for all the support on this thread.

---

