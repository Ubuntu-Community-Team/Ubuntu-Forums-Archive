---
title: "Calendar appindicator is missing"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by peterson43 on 2011-08-01
I recently installed Ubuntu 11.04. I've been messing around with it some to get things how I like them, and I just realized that there isn't a time of day displayed in the panel on the top right. I seem to remember it being there originally, but now it is gone. I think there is something called a calendar appindicator that I've somehow deleted and I can't find any information on where it is and how to re-install it. 

Some things that I've done that may have caused this problem are. 
1) I removed the indicator-me appindicator from the panel since I didn't use it. 
2) I completely removed Evolution since I use Thunderbird instead. Well actually, I followed the instructions at [http://ubuntu4beginners.blogspot.com/2011/06/replace-evolution-with-thunderbird.html](http://ubuntu4beginners.blogspot.com/2011/06/replace-evolution-with-thunderbird.html) which called for me to "completely remove" all but two of the packages with evolution in the name. 

Thanks for any help.

---

### Post by Frogs Hair on 2011-08-01
Welcome to UF !

```
sudo apt-get install idicator-datetime
```

If using Unity , it has no weather indicator.
```
sudo apt-get install indicator-weather
```

---

### Post by peterson43 on 2011-08-02
Thanks, this fixed the problem. The only thing to add is that I needed to restart my computer for the appindicator to show up on my panel.

---

### Post by peperomia on 2013-01-22
Just a trivial correction for the copy/pasters!

	sudo apt-get install idicator-datetime
should be
	sudo apt-get install indicator-datetime

---

### Post by peperomia on 2013-01-22
You don't have to restart to get the indicator back after install - you can just logout and back in again.

---

