---
title: "Removing OS from Hard Drive"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Scunnered on 2009-04-15
Another fine mess I have got my self into ! Going against my religon - DEVOUT COWARD, I decided to load Jaunty to my hard drive this morning. Initially things looked good but now I can't access my wireless connection. When working with the Live DVD all I had to do was click on the icon and enter a passwork and a connection was made. Now it shows up as disabled and no matter what I do it will not effect a connection. Left clicking on the icon only shows the wired network and nothing else.

This was the feature of Jaunty that I was very pleased to see as I had no end of problems with wireless connection in 8.10.

Now the question is how will I get rid of this troublesome Jaunty ? This is a dual boot with 8.10.

Your kind assistance will be appreciated.

PS. For the hell of it I returned to the Live session user mode and would you believe it I am back on line without any messing about. Left clicking on icon displays 4 networks and all the options and everything works.

---

### Post by kpkeerthi on 2009-04-15
If the Jaunty live CD works, it should be fixable. What wireless card do you have? 
Post the outputs of ```
lspci
``` ```
iwconfig
```

---

### Post by Scunnered on 2009-04-15
kpkeerthi

Many thanks for your reply.

After I posted I had another looki at things and came to the conclusion that a fresh install might just do the trick.  After messing about with the help I came to the conclusion that I should be able to delete the partition.  Checked this out and found that I could so on returning home within the last half hour I did a full install.

This time I was offered the choice of 4 wireless networks and after having to provide the password twice and totally switch off and a complete reboot the wireless connection was made.  I was totally surprised as on a post that I saw it said that the Atheros card was being supported in Jaunty.

I am now starting to see if I can set up Jaunty to meet my needs.

Once again many thanks for your assistance

---

