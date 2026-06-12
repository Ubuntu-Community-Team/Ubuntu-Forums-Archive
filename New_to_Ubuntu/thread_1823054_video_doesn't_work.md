---
title: "video doesn't work?"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by michey_n on 2011-08-11
i have a video with extension .wmv i tried to open it with movie player, it couldn't and started searching for suitable plugin but it didn't find any and it displayed this message


No packages with the requested plugins found
The requested plugins are:
video/x-asf-unknown decoder

i googled and someone suggested that i download vlc then i did, but it displayed this error

VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.

any help would be greatly appreciated, thanks...

---

### Post by sanderd17 on 2011-08-11
Can you go to the software center, enable the all package sources in the software sources and install the ubuntu-restriced-extras package?

---

### Post by papibe on 2011-08-11
Try installing this package: ubuntu-restricted-extras. It is on the software center, and also can be installed like this:
```
$ sudo apt-get update
$ sudo apt-get install ubuntu-restricted-extras
```
Try again playing the file.
Regards.

---

### Post by michey_n on 2011-08-11
thanks mates,
i tried the code but it didn't work..

---

### Post by papibe on 2011-08-11
Another alternative is to install another media player. Try either VLC or SMplayer. Both are in the Software Center.

Regards.

---

### Post by AgentZ86 on 2011-08-11
Also install all the Gstreamer stuff from the ubuntu software center.

That should fix it up for you.

---

### Post by LowSky on 2011-08-11
copy and paste this command into a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get install non-free-codecs
```

wmv should work now.

if not try logging out then back in and try again.

---

### Post by michey_n on 2011-08-11
> **LowSky said:**
> copy and paste this command into a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get install non-free-codecs
```

wmv should work now.

if not try logging out then back in and try again.

thanks, i tried what you said but it didn't work, i guess that the problem isn't in playing all wmv videos, i think that this video has a special codec and one thing i forgot to mention that it play sound only..

---

### Post by michey_n on 2011-08-11
> **AgentZ86 said:**
> Also install all the Gstreamer stuff from the ubuntu software center.

That should fix it up for you.

thanks, they are all installed...

---

### Post by michey_n on 2011-08-11
> **papibe said:**
> Another alternative is to install another media player. Try either VLC or SMplayer. Both are in the Software Center.

Regards.

thanks very much SMplayer worked :D

---

