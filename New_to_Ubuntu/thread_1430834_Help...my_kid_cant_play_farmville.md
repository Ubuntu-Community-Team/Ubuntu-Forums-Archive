---
title: "Help...my kid cant play farmville"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by demeter on 2010-03-15
hi there, this might be a silly question but I do really need help on this one...I have a machine that runs on jaunty and recently I upgraded it to karmic, as my son always bothers me whenever Im working on my other PC, I decided to set it up for him so that he could use it. problem is that he cannot play farmville on this? why is this so? Im a newbie to this OS and just learning on how to go about this so any help would be much appreciated....thank you very much....

---

### Post by sigurnjak on 2010-03-15
Do you have flash enabled ? If not google how to add ubuntu resricted codec and you should be good to go .

[http://www.medibuntu.org/](http://www.medibuntu.org/) 

It is all there . My wife plays both Yoville and Farmville .

---

### Post by sandyd on 2010-03-15
its a noted problem.
You need to install the 10.1 beta flash player.
```

sudo apt-get remove flashplugin-installer
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz
tar xvfz flashplayer10_1_p3_linux_022310.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

```

---

### Post by demeter on 2010-03-16
hi there, followed the instructions and still cant open farmville, it say's "The connection was reset"

      "The connection to the server was reset while the page was loading."...


thanks...

---

### Post by rigol2000 on 2010-03-31
Thanks Carlee!  I have not been able to play Yoville on Linux for a long time being forced to play on Windows.  Nothing I found worked until I came across your post.  Now it works in Ubuntu!

---

