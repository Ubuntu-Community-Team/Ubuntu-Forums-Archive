---
title: "Firefox not working"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by fooneyguy on 2010-08-22
Firefox is not working and I don't know why.

I had a restart issue and when Linux came back on it said there were memory issues I had it repair them and everything is working fine except for Firefox. The icon is broken and when I click it a warning comes up that says Firefox does not exist. Same thing when I try from the console.

Next I checked synaptic package manager which says Firefox is still installed. 

I would normally just start poking around or maybe uninstall and reinstall but I've learned my lesson with Linux and I don't want to screw something up.

If a re-install is the way to go that's just fine but I would like to know if there is a way to repair this for a couple of reasons. One I liked my Firefox setup, but I'm also trying to learn more about Linux and this seems like a great opportunity.

Thanks,
Sean

---

### Post by neilms on 2010-08-22
Type this at the command prompt:

neilms@shady:~$ whereis firefox

-----
after input of 'whereis firefox', I get this:

firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox

If you get the same then you can start firefox by entering the full path name at the command line or create another desktop link. If you dont get this out put, simply re-install firefox.

What is the problem with memory? How much Ram are you using?

---

### Post by lovinglinux on 2010-08-22
Try this:

```
sudo apt-get install --reinstall firefox
```

If that doesn't help see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

