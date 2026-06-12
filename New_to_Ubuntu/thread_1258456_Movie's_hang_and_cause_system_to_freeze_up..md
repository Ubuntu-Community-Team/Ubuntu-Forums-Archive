---
title: "Movie's hang and cause system to freeze up."
date: 2009-09-05
forum: New to Ubuntu
---

### Post by hnarwan on 2009-09-05
Hi All,

When playing movies over the my local network (wireless router connecting this machine Ubuntu Jaunty with an XP computer which holds my movie collection) after 10 minutes or so the movie player will freeze, the gvfsd-smb process shoots up to 50% CPU, when i kill it, i'm able to open progams again and open up my windows share and open my movie again, until again it freezes.

Any ideas? 

I never had this problem when this computer was running vista so the network connection is not the issue.

---

### Post by Kristofer Van Orton on 2009-09-05
im not sure i understand but are your using the ubuntu movie player?
maybe try vlc?
sorry im trying to be the best help i can

---

### Post by Liolikas on 2009-09-05
When playing movies over the my local network
Explain this in more details. Program names etc.
If you do not use VLC so really try it it has nice streaming solutions and was developed for that.

---

### Post by rsiddharth on 2009-09-05
Type this in Command line to install VLC :

```

sudo apt-get install vlc 

```

You will be prompted for **your **user account password after Entering the above command , please duly type it . 

Type this to get information about vlc : 
```

apt-cache show vlc 

```

VLC's site : [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

