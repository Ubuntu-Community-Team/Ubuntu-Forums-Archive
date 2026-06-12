---
title: "CoreAVC for Linux"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by barcelonic on 2009-10-19
I can get smooth 1080p playback on my Windows Vista but not through Ubuntu 9.04. I have a dual-booted system with each OS using a whole physical drive.

I have MPlayer and SMPlayer installed and set up gstreamer and w32 codecs but still no joy.

Then i found this....

[http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux](http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux)

Id be more than happy to pay the $15 for CoreAVC but this setup looks really complicated and may not even be applicable to 9.04.

So could somebody pls lay it out in easier terms to understand or paste the code i need to enter in the terminal to get this working? 

WIthout this im screwed as all i do on my PC is watch 1080p movies.

Any help would be enormously appreciated!!! :)

---

### Post by Bachstelze on 2009-10-19
[http://ubuntuforums.org/showthread.php?t=1034075](http://ubuntuforums.org/showthread.php?t=1034075)

---

### Post by barcelonic on 2009-10-19
> **Bachstelze said:**
> [http://ubuntuforums.org/showthread.php?t=1034075](http://ubuntuforums.org/showthread.php?t=1034075)

thanks. should i uninstall my current mplayer before doing this?

---

### Post by Bachstelze on 2009-10-19
> **barcelonic said:**
> thanks. should i uninstall my current mplayer before doing this?

You should, since you won't be using it anymore anyway, but you don't *have* to. It's covered in the FAQs at the bottom.

---

### Post by 3rdalbum on 2009-10-19
If you have an Nvidia graphics card, there is another option: VDPAU.

As far as I know this still requires recompiling Mplayer with the "--enable-vdpau" option, and installing the vdpau-related packages in Synaptic, but it offloads a lot of the decompression and display to your Nvidia card. It really makes a difference.

Also, I just noticed that I get stuttery VC1 playback with Compiz on, but smooth playback with Compiz off. Give that a try maybe :-)

---

### Post by barcelonic on 2009-10-19
> **Bachstelze said:**
> You should, since you won't be using it anymore anyway, but you don't *have* to. It's covered in the FAQs at the bottom.

HI mate im nearly at the end of your guide, which btw is really good and helpful so thx, but im having the same problem that BrownD on page 1 had.

I had loads of errors when building mplayer.

Should i just ignore it or will mplayer not work? If not what should i do now? Im going to leave the terminal as it is until u reply as i dont wanna mes things up cus everythings gone as planned so far.

Thanks

---

### Post by Bachstelze on 2009-10-19
Is this the message you're getting?

```
libavcodec/libavcodec.a(pcx.o): In function `pcx_decode_frame':
pcx.c:(.text+0x94a): warning: memset used with constant zero length parameter; this could be due to transposed parameters

```

If it is, just proceed, you should be fine. It is actually a warning, not an error.

---

### Post by barcelonic on 2009-10-19
Actually these are the warnings...

[I]libmpdemux/muxer_avi.c:481: warning: passing argument 2 of 'stream_write_buffer' from incompatible pointer type

xvid_vbr.c:703: warning: ignoring return value of 'fscanf', declared with attribute warn_unused_result

cfg-common-opts.h:176: warning: initialization discards qualifiers from pointer target type

swscale_template.c:2747: warning: cast from pointer to integer of different size

swscale_template.c:1243: warning: dereferencing type-punned pointer will break strict-aliasing rules[/I]

And a few more:
[I]
aes.c:84: warning: passing argument 2 of 'mix' from incompatible pointer type
aes.c:85: warning: passing argument 1 of 'addkey' from incompatible pointer type
aes.c:85: warning: passing argument 2 of 'addkey' from incompatible pointer type
aes.c:85: warning: passing argument 3 of 'addkey' from incompatible pointer type
aes.c:87: warning: passing argument 1 of 'subshift' from incompatible pointer type
aes.c: In function 'av_aes_crypt':
aes.c:92: warning: passing argument 1 of 'addkey' from incompatible pointer type
aes.c:92: warning: passing argument 2 of 'addkey' from incompatible pointer type
aes.c:92: warning: passing argument 3 of 'addkey' from incompatible pointer type
aes.c:94: warning: passing argument 4 of 'crypt' from incompatible pointer type
aes.c:96: warning: passing argument 1 of 'addkey' from incompatible pointer type
aes.c:96: warning: passing argument 2 of 'addkey' from incompatible pointer type
aes.c:96: warning: passing argument 3 of 'addkey' from incompatible pointer type
aes.c:99: warning: passing argument 1 of 'addkey' from incompatible pointer type
aes.c:99: warning: passing argument 2 of 'addkey' from incompatible pointer type
aes.c:99: warning: passing argument 3 of 'addkey' from incompatible pointer type
aes.c:101: warning: passing argument 1 of 'addkey' from incompatible pointer type
aes.c:101: warning: passing argument 2 of 'addkey' from incompatible pointer type
aes.c:101: warning: passing argument 3 of 'addkey' from incompatible pointer type
aes.c:102: warning: passing argument 4 of 'crypt' from incompatible pointer type
aes.c:103: warning: passing argument 1 of 'addkey' from incompatible pointer type[/I]

---

### Post by Bachstelze on 2009-10-19
As long as it's just warnings (no errors), you should be fine. What do the few last lines of the make output look like?

---

### Post by barcelonic on 2009-10-19
> **Bachstelze said:**
> As long as it's just warnings (no errors), you should be fine. What do the few last lines of the make output look like?

install -d /usr/local/bin /usr/local/etc/mplayer /usr/local/lib
install -m 755 -s mencoder /usr/local/bin
install -d /usr/local/share/man/man1
install -m 644 DOCS/man/en/mplayer.1 /usr/local/share/man/man1/
cd /usr/local/share/man/man1 && ln -sf mplayer.1 mencoder.1
install -m 755 -s mplayer /usr/local/bin

---

### Post by Bachstelze on 2009-10-19
That was make install. ;) But anyway, if make install worked at all, it means that the build was successful.

---

### Post by barcelonic on 2009-10-19
I got to the end and tried to check its working by launching from terminal but it opens the file in terminal not in GUI player.

why is that?

and also which config file do i edit and where in the document should i add that code?

---

### Post by Bachstelze on 2009-10-19
Are you sure the file you're trying to play has an H.264 video stream?

---

### Post by barcelonic on 2009-10-19
> **Bachstelze said:**
> Are you sure the file you're trying to play has an H.264 video stream?

Yes.

Also there is no MPlayer in the Apps menu and when you choose OPen With on a video file there is no option to use MPlayer. It looks as though its not installed, but it must be because the terminal ran that movie file. :confused:

---

### Post by barcelonic on 2009-10-19
What if i installed mplayer through package manager?? Would that end up conflicting with the install i tried in the terminal?
And if not, would it work in tandem with coreavc?

EDIT:
I just realised something..  when i tried to build the program i pasted in the following:

make
sudo make install

instead of doing each line separately i did them together and the ensuing process took 5 minutes to complete!!

i just tried them separately now and it seemed to work, but whatever i did before may have caused a problem because i still cant access MPlayer gui. The mkv file simply opens in the terminal, and it definitely is H264.

so im pretty much stuck now. any ideas?

---

### Post by barcelonic on 2009-10-19
any help please anyone? i tried the guide but now im totally stuck! :(

---

