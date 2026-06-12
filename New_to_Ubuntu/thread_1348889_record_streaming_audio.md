---
title: "record streaming audio"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by amarumayo on 2009-12-07
Does anyone know how to record streaming audio. I have tried everything and can't get it to work.

Thanks

---

### Post by bodhi.zazen on 2009-12-07
What have you tried ?

You can try streamripper ?

It is in the repos

[http://streamripper.sourceforge.net/about.php](http://streamripper.sourceforge.net/about.php)

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=streamripper](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=streamripper)

---

### Post by drz4007 on 2009-12-07
i use streamtuner. i dont know if its the same.

---

### Post by ajgreeny on 2009-12-07
You can do it best in terminal using either mplayer and/or streamripper, depending on your stream type.  Here are two examples from UK which I use for recording with mplayer, with ease.
```
mplayer <URL> -dumpstream -dumpfile stream.mp3
```
                    saves mp3 stream as file stream.mp3
```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
```
                    saves real or other stream as file outfile.wav.  You can also convert it to an mp3 with ffmpeg if you wish

I use them adapted as a shell script, which I can then cron to time a recording of a concert, or other music.  Note my need to add the **-playlist** before the URL for BBC real streams, which may or may not be needed for all streams.  Try it with and without if it doesn't work first time.

```
#!/bin/bash
/usr/bin/mplayer -cache 2048 -playlist URL -vc null -vo null -ao pcm:fast:waveheader:file=$(date +%F-%I%M)-BBCR2.wav &
# Uncomment the line below for the time in minutes to record
# or copy from the "# sleep" and add to end of line above ending with &
# sleep 32m; killall mplayer
# sleep 47m; killall mplayer
# sleep 62m; killall mplayer
# sleep 92m; killall mplayer
# sleep 122m; killall mplayer
```

For streamripper mp3 stream recording, the script is:-
```
#!/bin/bash
/usr/bin/streamripper URL -t -d /home/user/Radio -l 3720
```
The -l 3720 is the number of seconds it records, ie in this case 62 mins.

---

### Post by bodhi.zazen on 2009-12-07
> **drz4007 said:**
> i use streamtuner. i dont know if its the same.

No, it is not the same, but I believe made by the same group and integrates with streamtuner.

---

