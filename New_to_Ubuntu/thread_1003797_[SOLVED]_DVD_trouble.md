---
title: "[SOLVED] DVD trouble"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-06
Just installed 8.10 and cannot play proprietary movies, (one's you buy). I have tried totem, VLC and mplayer with no success? what do I need? thanks in advance

---

### Post by wolfen69 on 2008-12-06
go to system>administration>software sources and make sure all repos are checked off, then reload. check third party tab also. then do ```
sudo apt-get install libdvdcss2
```

---

### Post by s.fox on 2008-12-06
It might be an idea to add the Medibuntu Repository

Medibutu stands for Multimedia, Entertainment & Distractions In Ubuntu and is a repository of packages that cannot be included in Ubuntu due to legal reasons. You may need to add this repository to enable MP3, DVD playback, install certain codecs etc.  More info can be found [here]("https://help.ubuntu.com/community/Medibuntu")

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update 
sudo apt-get install medibuntu-keyring 
sudo apt-get update
```

hope this helps you with your DVD troubles

---

### Post by som1special2 on 2008-12-06
doesn't work, says item is obselete. checked synaptic and no go there either.

---

### Post by wolfen69 on 2008-12-06
post the output of ```
cat /etc/apt/sources.list
```

---

