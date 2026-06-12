---
title: "How to make new launchers?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-20
First I'm not sure "launcher is the right word. What I mean is a new Icon on my bar that launch an application. For i.e. I want a new one for JDownloader, which I use to download from file hosters like megaupload, rapidshare, ect...
Now I have the script file which I made executable from properties but I'd like to have the icon and that it wont prompt me each time asking if I want to just show content or execute the script.
How do I find out which is the right command for an application? What if I want a new one for OpenOffice? I know how to create it, right click on the bar and click "add new launcher"...but How do I find the right command to put in?

---

### Post by WinterRain on 2010-05-20
In lucid, if that's what you're using, there's no need to enter a command. Click add to panel, then the second choice down is application launcher. Then click forward and select your app. Or you can simply go to the menu item and drag it to the panel.

---

### Post by angry_johnnie on 2010-05-20
in this case, given the fact that you have a custom script, you would click on the panel, select add to panel, add new launcher, and the command for that launcher would just be the path to your script.

for instance, if your script is in your home directory, the command to launch that script is
```

/home/you/script
```

pretty straight forward, once you've done it ;)

---

