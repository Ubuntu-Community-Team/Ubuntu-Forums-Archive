---
title: "Do I have to update?"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Nutbun on 2011-03-06
After a fresh install of Ubuntu, there are usually a few hundred updates to be downloaded and installed.

Is it recommended that I install these updates or leave things as they are?
Same for future updates.  If everything is working okay should I still download updates, what is the done thing?

---

### Post by bioterror on 2011-03-06
Software gets bug fixed and updated.
I would recommend, but if you feel it works just fine like that, why to try fix something that's working?

And security fixes ofcourse are welcome to any system.

---

### Post by maqtanim on 2011-03-06
This updates contain bug fixes, security upgrades, new enhancements of existing softwares and lot more. So yes it is RECOMMENDED to update the system.

---

### Post by mmsmc on 2011-03-06
if you are using the internet, it is highly recomended, these updates are why linux is famous, and is the reason why linux gets so few viruses

---

### Post by Nutbun on 2011-03-06
My thanks.  It seems it always wants to update I have 4 different selections of Ubuntu in my boot menu already, I was wondering how necessary the updating was. :)

---

### Post by kaldor on 2011-03-06
If you update to the newest Ubuntu every 6 months, then the updates are less needed. Sometimes updates have been known to cause problems. If you're getting along just fine, leave it as is if you feel any doubts.

You can, however, update just a single package. 

For example, update your Firefox with this command in the terminal:

```
sudo apt-get update && sudo apt-get install firefox
```

That will update Firefox and its dependencies without updating all of your system.

---

### Post by mikewhatever on 2011-03-06
Installing updates is recommended because of this -> [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn).

---

### Post by el_koraco on 2011-03-06
> **Nutbun said:**
> I have 4 different selections of Ubuntu in my boot menu already, I was wondering how necessary the updating was. :)

what you have is 4 different generic linux kernels (the core on which the whole os is built). you can remove the old kernels you're not using. first type 

```
uname -a 
```

in the terminal, which will show you which kernel you're currently using. then you can go to synaptic and remove some of the old kernels. it's usually good to keep the last recent kernel, in case you need to switch back. type linux-image-2 in synaptic, whereupon you can find your old kernels. you can then remove them. make sure you do not remove your current kernel, the one you found by typing uname in the terminal, or else you'll cause yourself all kinds of problems.

---

### Post by C_M_L on 2011-03-06
I would definitely update. I just loaded the latest version and as much as worked OK, I needed the additional update in order to download the appropriate plug-ins and other stuff like CODECS. It was about 350Mb of updates and that is a lot if you have a slower connection. Mine was down and installed in about 45 minutes.

---

### Post by Nutbun on 2011-03-07
Thank you for all of your excellent advice, it has put my mind at ease.
I will carry on updating when ever they are available, it only takes a minute or two. I will also clear some of my old kernels before they run of the bottom of my boot page. :)

BTW: It's a great community you have here.

---

### Post by ubudog on 2011-03-07
> **Nutbun said:**
> After a fresh install of Ubuntu, there are usually a few hundred updates to be downloaded and installed.

Is it recommended that I install these updates or leave things as they are?
Same for future updates.  If everything is working okay should I still download updates, what is the done thing?

It's always recommended to update the system.

PS: Yes, the community here is very strong.  Just ask anything, and one of us will respond.  :P
Always remember that no question is stupid.

---

### Post by 3177 on 2011-03-07
depends, 
did you install WITH Internet?
If not you should DEFINITELY install those updates.
Ubuntu's secure for a reason.

---

