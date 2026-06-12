---
title: "Keyboard and mouse recorder Macro"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-08-30
Hello,

Can anyone suggest a program i can use for a keyboard and mouse recorder? i use to use a program called EZ macro when im using windows for a game im playing but i seem not to find anything similar for linux?

---

### Post by nhasian on 2009-08-30
take a look at:

[http://www.gnu.org/software/xnee/](http://www.gnu.org/software/xnee/) 
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

---

### Post by vlad1975 on 2009-08-30
thank you

---

### Post by Barbara0415715 on 2009-08-31
I heard there are some problems with both the programs:

About xmacro: [https://bugs.launchpad.net/ubuntu/+source/xmacro/+bug/367685](https://bugs.launchpad.net/ubuntu/+source/xmacro/+bug/367685)

About Xnee: in 2008 erginemr said: "I have also tried it and it seems to crash whan you start recording" ([http://ubuntuforums.org/showthread.php?t=667181&highlight=gnee](http://ubuntuforums.org/showthread.php?t=667181&highlight=gnee)).

I've the same problem  when I try to record in gnee or cnee. I get error 35: "Record memory failure - Xnee failed due to bad data received from RECORD extension".

Does someone knows a solution? Or maybe another program?

---

### Post by mally on 2009-10-05
I've been trying to figure out the same problem.  I read that GhostMouse works perfectly in Wine, now, but when I record my macro, the playback goes through the correct moves except that it doesn't click as it should.  I'd sure appreciate any solutions anyone might have found, either as a fix for this issue, or another application that doesn't require the terminal.

---

### Post by PGScooter on 2010-01-03
xnee is now working great for me in 9.10:

Here is a link to 3.05, released a week ago, if you're interested:

[http://www.sandklef.com/hesa/index.php/2009/12/24/gnu-xnee-3-05-merry-x11-mas-released/](http://www.sandklef.com/hesa/index.php/2009/12/24/gnu-xnee-3-05-merry-x11-mas-released/)

---

### Post by dubref on 2010-02-22
PGS was there anything special you had to do to get xnee working?

I keep getting segfaults when recording.

I removed old version, which used to work so splendidly a few Ubuntus back( I think it was 8.04 when it worked for sure).
```
sudo apt-get remove xnee
```

Downloaded xnee 3.05 from [http://ftp.gnu.org/gnu/xnee/xnee-3.05.tar.gz](http://ftp.gnu.org/gnu/xnee/xnee-3.05.tar.gz)

did ./configure
had to ```
./configure --disable-gui --disable-gnome-applet
```
because it could not find newest libgnomeui 2.24 which Ubuntu 9.10 has.

Still this should not matter, as all I would need would be simple cnee.
To install, did the usual ```
make
``` and ```
make install
``` 

Now even simple example recording:
```
cnee  --record  --events-to-record  100  --mouse  --keyboard -o ~/xnee.xns -e
       ~/xnee.log -v
``` ends up with seg fault

*Sleep workaround a strange RECORD/Xtest problem around 2009 (ignore it)* is one possible error message before segfault.

Anyone have better experience lately with xnee?

---

### Post by PGScooter on 2010-02-22
hi dubref,

I wish I could help but I have no ideas. You should contact the author. He is very nice and I think he would appreciate the bug report. Let us know what happens.

---

### Post by hesa on 2010-05-26
The problem seems to be solved: 

   [http://lists.gnu.org/archive/html//bug-xnee/2010-05/msg00015.html](http://lists.gnu.org/archive/html//bug-xnee/2010-05/msg00015.html)

/hesa

and btw, support for multiple and simultaneous devices have just been added to Xnee:
  
  [http://itupw056.itu.chalmers.se/xnee/special-dist/xinput/xnee-3.05-xinput-0.1.tar.gz](http://itupw056.itu.chalmers.se/xnee/special-dist/xinput/xnee-3.05-xinput-0.1.tar.gz)

---

### Post by dubref on 2010-05-27
Hesa thanks so much for the reply and most of all the work you guys have been doing on xnee!

**TL;DR Cnee works now, gnee crashes.**

Finally a successful run.

Downloaded source you suggested
[ftp://alpha.gnu.org/gnu/xnee/xnee-3.05.92.tar.gz](ftp://alpha.gnu.org/gnu/xnee/xnee-3.05.92.tar.gz) 

and managed to get a working cnee.

There were some small snags on the way, though, nothing major.

```
./configure
```
didn't pick up that one would need gnome.h
so had to figure out package for that by myself

```
sudo apt-get install libgnomeui-dev

```

after completing successful ```
make
```

[cnee recording and playback works fine (and this is all I really need)

However, gnee crashes
```
~/xn/xnee-3.05.92$ which gnee
/usr/local/bin/gnee
```

```
~/xn/xnee-3.05.92$ gnee

** (gnee:9619): WARNING **: Couldn't find pixmap file: xnee.xpm

(gnee:9619): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
```
[I]
repeat (gnee:9619) bunch of times now

and now the biggie[/I]
```
*** glibc detected *** gnee: free(): invalid next size (fast): 0x095b9bb0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb69d9591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0xb69dade8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb69ddecd]
gnee[0x804cda5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb6984bd6]
gnee[0x804c921]
======= Memory map: ========
long list snipped

```

If I had to make a wild guess, I'd say some package used in compiling was not exactly the right one, I didn't go through the whole configure and make output.. 


PS I have a rather vanilla install of Ubuntu 10.04 (using old style <=9.10 appearance though).

---

### Post by hesa on 2010-06-17
We are currently working on the bugs reported here. For status, check here:

  [http://savannah.gnu.org/bugs/?30134](http://savannah.gnu.org/bugs/?30134) 
  [http://savannah.gnu.org/bugs/?30136](http://savannah.gnu.org/bugs/?30136)
  [http://savannah.gnu.org/bugs/?30137](http://savannah.gnu.org/bugs/?30137)

/hesa

---

### Post by hesa on 2010-06-28
Can you tell me what you did to crash gnee?

I'll try to fix it asap

/hesa

---

### Post by dubref on 2010-06-29
Hesa,
  I unpacked source from [ftp://alpha.gnu.org/gnu/xnee/xnee-3.05.92.tar.gz](ftp://alpha.gnu.org/gnu/xnee/xnee-3.05.92.tar.gz) then: 
```
./configure
make
sudo make install
gnee
```
I should note, that I have not really used gnee before (my cnee scripts work fine :) )

Here is the stuff that configure reports as missing (but which I have installed):

[FONT="Courier New"]dia
texi2html
texline-base (dvipdf)
ghostscript (ps2pdf)
texline-font-utils (epstopdf)[/FONT]

What configure says:
```
   Programs used to build documentation and/or guis 
   -----------------------------------------------------
       ***** dia missing, Can't generate pictures from dia sources
       convert  - /usr/bin/convert
       ***** texi2html missing, can not generate html pages
       ***** dvipdf missing, can not generate pdf from dvi 
       ***** ps2pdf missing, can not generate pdf
       ***** epstopdf missing, can not generate pdf
       convert  - /usr/bin/convert
       makeinfo  - ${SHELL} /home/dubref/xn/xnee-3.05.92/autotools/missing --run makeinfo
       pkg-config  - /usr/bin/pkg-config

   Building the following components 
   -------------------------------------
    
        cli
        gnee
        pnee 
 
   Excluding the following components 
   -------------------------------------
    
        doc (docs are already included in dist file)
``` 

Also, if it helps any, I have pasted the whole error output gotten when running gnee to [http://pastebin.com/mmNVpd1M](http://pastebin.com/mmNVpd1M) 
It is pretty much the same thing as what I posted in the last post.

If there is anything else to do, I'd be glad to help.

---

### Post by hesa on 2010-07-15
Can you tell me:

* how you started gnee
* does gnee crash when recording or replaying?
* exactly what buttons/settings/.... did you use before clicking record or replay?
* if you could record, please attach (not using pastebin or similar .. for archive reasons) the recorded file 


/hesa

---

### Post by dubref on 2010-07-19
After compiling, I simply typed **gnee** at the command line and program crashed with the error output I showed a few posts back.

 That is I never got to GUI part and did not get to record or play back anything from gnee...

---

### Post by hesa on 2010-07-30
Can't reproduce the problem with gnee (in Debian).

WIll see later on in August, at home, if I can reproduce the error there and report back to Xnee or Ubuntu or ....


Meanwhile, can you start gnee in gdb, typically sth like:

  gdb ./gnee/src/gnee

and then (in the gdb window) type:

  run

and when gnee crashes you can get the backtrace, like this:

  bt 


If you, then, can copy/paste the backtrace to this forum, it'll help a lot

---

### Post by xylometazolin on 2010-12-14
Hi,

I compiled cnee 3.07 using the sources available at [http://savannah.gnu.org/](http://savannah.gnu.org/).  Under Ubuntu Lucid everything works fine, especially recoding events.  Under Ubuntu Maverick the compilation and start of cnee works also fine, but I cannot see any events recorded, neither keyboard events nor mouse events.  Both tests have been performed on different computers with different Xorg configurations.  Do I have to enable a special extension in my xorg.conf for being able to record events?

The RECORD extension is not needed anymore, I thought.  It's also not enabled on my Lucid machine where cnee works.

Stefan

---

### Post by nsk7even on 2011-04-20
Hello,

is there a beautiful How To out there for using cnee/gnee?

Or are there known incompatibilities to current Maverick?


Because either I am too silly to use them or they are not working for me:
- Gnee closes after doing the first few clicks. The terminal tells something about loops until I press Strg+c
- cnee logs me out after doing the first few clicks and I don't know what is happening


Any help?

7even

---

### Post by PGScooter on 2012-01-24
Xnee/gnee/ 3.11 was just released last month. I'd be curious to know if it solved some of the problems people have been having. A few bug fixes seem specifically targeted at Ubuntu.
announcement:
[http://sandklef.wordpress.com/2011/12/16/gnu-xnee-3-11-jansch-released/](http://sandklef.wordpress.com/2011/12/16/gnu-xnee-3-11-jansch-released/)
downlaod:
[http://ftp.gnu.org/gnu/xnee/](http://ftp.gnu.org/gnu/xnee/)

---

