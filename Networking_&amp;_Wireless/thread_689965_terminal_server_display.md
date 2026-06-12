---
title: "terminal server display"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by akahige on 2008-02-06
I have a few Windows machines that I use the Terminal Server Client to connect to via RDP (from Gutsy, now). I've been running a single monitor at 1680x1050 and everything works just fine.

I just upgraded to a dual head video card and an identical second monitor, and am working out the kinks in the various ways that things display.

The thing that I'm facing at the moment is the behavior of Terminal Server Client (or whatever it's front-ending). Running only one monitor, I could simply choose the "operate in full screen mode" option and everything was fine. Now, if I do that, I get a dual monitor display which I don't want.

There's a drop down with various preconfigured screen sizes -- none of which are quite what I want. I'd like to be able to edit this to create a screen size that approximates one of the monitors so I can monitor a remote machine at a decent screen size while working on my Xubuntu desktop.

Did some hunting around on the forums and couldn't find anything, so I'm hoping someone can point me in the right direction.

Thanks!

---

### Post by stone@bruti on 2008-02-07
Hy

Try executing
"rdesktop -g AxB xxx.xxx.xxx.xxx: xx"  (no space betwen IP and Port, had to put it or I get a smily :s )
where
AxB is your window size (800x600)
xxx.xxx.xxx.xxx: xx is your Terminal serveur IP adresse and port (192.168.0.1:3389)

if not, do a "man rdesktop" in a terminal to get all the possible options

this forces the windows size to whatever values you want. Be careful if using desktop features from Compiz-fusion, I had a few probs when in full screen moad.

hope this helps

Stone

---

### Post by akahige on 2008-02-07
Thanks for the help! That worked great!

---

