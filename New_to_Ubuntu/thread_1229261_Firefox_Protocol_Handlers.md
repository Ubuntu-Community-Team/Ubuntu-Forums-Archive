---
title: "Firefox Protocol Handlers"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by HiImTye on 2009-08-01
ok, so I installed the palace (or rather, unzipped it as the install doesn't work, hangs at searching for installed files), visual chat program which works just fine (aside from the poor handling of palettes in every editing program, even PSP9 ran through WINE). Now, I want to open a link in Firefox with a 'palace://' protocol but I receive an error such as 'firefox cannot open the link because there is no known associated program' or some such thing. here is a short list of what I have done so far:

terminal: tye@T:~/~$ gconftool-2 --set /desktop/gnome/url-handlers/palace/command --type="string" "/media/20gig/Windows Files/ThePalace/Palace32.exe"
firefox: about:config > network.protocol-handler.app.palace;'/media/20gig/Windows Files/ThePalace/Palace32.exe' (tried with and without apostrophes)

any suggestions?

---

### Post by gali98 on 2009-08-03
I know absolutely nothing about what you're doing.. :)
But I do know that you can't just point to the .exe...
So try adding "wine " before the path to the .exe and see if that does something for you...
Kory

---

### Post by HiImTye on 2009-08-03
way to make me feel stupid lol

but still no go after changing it to what I had it in my launcher

---

### Post by gali98 on 2009-08-04
haha... :)

Well I guess you could point me to where you learned how to do this, and I could go over it to see if I can find anything out?
Kory

---

### Post by HiImTye on 2009-08-04
I can't seem to find the page again but it basically goes like this

about:config

new > string
type in 'network.protocol-handler.app.protocol' (replacing 'protocol' with the text of the protocol, i.e. apt for apt:// links)
type in the path to the program launched

that's the entirety of the instructions. I'm not sure how you would work this with WINE, was hoping someone would know

---

### Post by gali98 on 2009-08-05
Okay, I think I found a way to do it...
First I made a shell script like so:

```
#!/bin/sh
/usr/bin/wine /path/to/exe
```

Then make it executable like so:
```
chmod +x /path/to/script
```

then make the protocol string like so:
```
/path/to/script
```

then when you use the protocol like
protocol://blah.blah
it will open up a window... for some reason you have to say click on the button and go find the shell script and run it like that.. I only had to do it once...
Try it and see if that works...

---

### Post by HiImTye on 2009-08-16
using a shell script doesn't seem to work, I get these results:

when run as /home/<username>/palace.sh, ~/./palace.sh it sits there and does nothing
when run as ./palace.sh (like with the alt+f2 run dialogue) I receive the previous error

also, when testing the script wine doesn't seem to pass on the variable to the program. here's my script in case you guys have any suggestions:

```
#!/bin/sh
wine D:\\ThePalace\\Palace32.exe $1
```

---

