---
title: "Lost video codecs???"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by TheBuzzSaw on 2009-11-02
I attempted installing OpenShot using the PPA repository. The program would just freeze upon running, so I decided to get rid of it.

Now, I cannot play *any* of my videos that I have. How do I go about repairing my video codecs? Not even VLC will play any of my videos. T_T

Help!

UPDATE -- Great. I'm not the only one. [https://bugs.launchpad.net/openshot/+bug/466697](https://bugs.launchpad.net/openshot/+bug/466697)

---

### Post by 3rdalbum on 2009-11-02
The problem is that the Openshot PPA overwrites the ffmpeg and libav* packages.

First, disable the Openshot repository. Next, you need to use Synaptic to FORCE VERSION the libav* packages to their regular Ubuntu versions. If you FV one and it tells you that it will remove a lot of programs, then click cancel and try FVing the next one. If you do it in the correct order, you will not lose any packages and your system's video playback will be back to normal.

---

### Post by TheBuzzSaw on 2009-11-02
I got everything fixed finally. Thank you for the help!

---

