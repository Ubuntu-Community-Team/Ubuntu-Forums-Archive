---
title: "VLC and Xauthority"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Mwelsh on 2011-07-15
I want to be able to control linux from an SSH session remotely, and have that session be able to start a graphical VLC on the box I SSH to.

Based on this: [http://ubuntuforums.org/showthread.php?t=411622](http://ubuntuforums.org/showthread.php?t=411622)

I have used that script, but I need to sudo. VLC cannot be run as a root user.

I tried to follow the steps here [http://www.microdevsys.com/WordPress/2010/07/12/vlc-videolan-video-player-failed-to-connect-to-the-d-bus-session-daemon-bindbus-launch-terminated-abnormally-with-the-following-error-no-protocol-specified/](http://www.microdevsys.com/WordPress/2010/07/12/vlc-videolan-video-player-failed-to-connect-to-the-d-bus-session-daemon-bindbus-launch-terminated-abnormally-with-the-following-error-no-protocol-specified/)

However, I could not find a /root/.XAuthority file.

Any suggestions?

Thanks in advance, Ubuntu community is awesome.

---

### Post by Mwelsh on 2011-07-15
Of course after searching for hours, I came across a solution 5 seconds after posting.

```
xhost +
```

While not safe, it works. And since this is internal network only, the solution is ok for me.

Thanks!

Mike

---

