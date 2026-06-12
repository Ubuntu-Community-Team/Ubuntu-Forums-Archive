---
title: "a JPG VIEWER with refreshing every sec ?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-05-30
```


$ while [ 1 ] ; do fswebcam -d /dev/video1 image.jpg ; done
```

Is there a program that can show the jpg with refreshing the jpg every seconds? 
EOG cannot do that :(

---

### Post by kaibob on 2010-05-30
> **frenchn00b said:**
> Is there a program that can show the jpg with refreshing the jpg every seconds? 
EOG cannot do that :(

You can use feh, a lightweight image viewer. The -R option in the following command reloads file.jpg every 3 seconds. 

```
feh -R 3 file.jpg
```

I don't believe feh is installed by default, but it's in the repo's.

BTW, I am not familiar with fswebcam and don't know how feh would work within the context of your command.

---

