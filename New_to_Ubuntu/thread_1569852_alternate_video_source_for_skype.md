---
title: "alternate video source for skype"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by sam-bo on 2010-09-07
I'm trying to have write permission on "home/user/.Skype/login/config.xml".  since skype uses "/dev/video0" I would like to make it use "/dev/video1" instead. 

any suggestions?

---

### Post by cavh on 2010-09-07
```
sudo gedit /home/user/.Skype/login/config.xml
```

---

### Post by sam-bo on 2010-09-07
all I get is a blank page entitled "config.xml"

---

### Post by cavh on 2010-09-07
In that case the file doesn't exist. Are you sure that's the right path? Is 'user' in the path correct - or should it be something like your name? Please post the output of 

```
sudo ls /home
```

---

### Post by LowSky on 2010-09-07
replace user with you login name
so if sam-bo is your login name
```
sudo gedit /home/sam-bo/.Skype/login/config.xml
```

---

### Post by sam-bo on 2010-09-07
yes,

example:
but no sign of "/dev/video0"
    
sudo gedit /home/sam-bo/.Skype/myskypeusername/config.xml

---

### Post by sam-bo on 2010-09-07
the only thing with video is:


    <Video>
      <AutoSend>0</AutoSend>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>

Im not sure where to change "/dev/video0" to "/dev/video1"

---

### Post by sam-bo on 2010-09-07
All I would like to do is change the skype default video source to "/dev/video1" so that it deosnt use "/dev/video0".

---

