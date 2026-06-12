---
title: "VLC media player crashes in 5 mins"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by kfkehua on 2011-05-11
newly installed ubuntu 11.04, installed vlc player. when watching some movies with VLC, it crashes within 5 mins. is anybody having this problem?

---

### Post by packpunk on 2011-05-12
Yes, I had the same problem too... :(

---

### Post by astex on 2011-05-12
I'll need a little more information to help with this.  Open a terminal and type:

```
$ vlc -v
```

Copy and paste the last ten or so lines before the crash.

---

### Post by mohiz on 2011-05-13
I have the same problem I think... it hangs and I have to kill it. It's too bad, because vlc is the best player.

---

### Post by david-b on 2011-05-17
dbelanger@Biostar:~$ vlc -v
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9d02914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1305479672)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:6437): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
------------
Ubuntu 11.04 and vlc 1.1.9
whenever I use vlc, to play .avi or mkv files, it logs me off, not reboot
It used to work great with ubuntu 10.4
Can anyone tell me how to fix this issue?

Thanks in advance.
Dave

---

### Post by ayushb2k on 2011-05-20
> **astex said:**
> I'll need a little more information to help with this.  Open a terminal and type:

```
$ vlc -v
```Copy and paste the last ten or so lines before the crash.

[COLOR=Red][0xa0b5834] main audio output warning: audio drift is too big (225773636), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225752303), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225730970), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225709636), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225688303), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225666970), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225645636), dropping buffer
[0xa0b5834] main audio output warning: audio drift is too big (225624303), dropping buffer[/COLOR]
[0xa0b5834] main audio output warning: PTS is out of range (5188397), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5167574), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5146721), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5125864), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5104995), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5084122), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5062911), dropping buffer
[0x9e3519c] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0xa00d574] main video output warning: late picture skipped (5139873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5181873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5222873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5097873 > -1948 ) 
[0xa00d574] main video output warning: late picture skipped (4930873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5014873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5055873 > -1948 ) 
[0xa00d574] main video output warning: late picture skipped (4972873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (4889873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5598873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5681873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5639873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5431873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5514873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5556873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5472873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5264873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5347873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5389873 > -1948 )
[0xa00d574] main video output warning: late picture skipped (5306873 > -1948 )
[0xa0b5834] main audio output warning: PTS is out of range (5043600), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5022746), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (5002042), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4981278), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4960408), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4939721), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4918848), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4898654), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4877777), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4856899), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4836054), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4815390), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4794516), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4773807), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4752945), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4731724), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4710869), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4689995), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4669247), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4648371), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4629342), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4608488), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4587613), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4566429), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4545562), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4524693), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4504017), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4483152), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4462291), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4441426), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4420658), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4400570), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4379705), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4358889), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4338161), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4317381), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4296612), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4276178), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4255496), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4234296), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4213623), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4192962), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4172115), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4151227), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4130350), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4109474), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4088615), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4067473), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4046653), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4025599), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (4004526), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3983382), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3962235), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3941090), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3919942), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3899509), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3878431), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3857285), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3836134), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3814988), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3793840), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3772691), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3751554), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3730074), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3708927), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3687806), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3666659), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3645659), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3624525), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3603450), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3582304), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3560823), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3539679), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3518534), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3497386), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3476256), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3455111), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3433965), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3412816), dropping buffer
[0xa0b5834] main audio output warning: PTS is out of range (3392341), dropping bufferKilled


hi, Pasted above... i think the RED colored lines are the culprit lines ... as the lines after that came, when i tried killing the process as my system hanged-out completely... in a desperate attempt i pressed Ctrl+C many times......which finally killed VLC.

~ayush

---

### Post by Koffeehaus on 2011-06-23
Yes, I switched back to 10.10 because of this thing. Well, there were other bugs, but mainly cos of this....

---

### Post by alphacrucis2 on 2011-06-23
Have you tried vlc 1.1.10.

---

