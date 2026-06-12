---
title: "Rec mic: Please how to pipe arecord with lame to make mp3 ?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-10
```
		arecord -Dplughw:3,0 -f cd -vv | lame -x - $FILENAME2MP3
	else
		arecord -Dplughw:3,0 -f cd -vv "$FILENAME2"
```

the second method with lame is not working :(

---

