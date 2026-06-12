---
title: "Lirc errors whenever I try to install things/work in terminal"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by panasonicyouth on 2009-09-01
Hello,

Absolute ubuntu/linux noob. Running jaunty (9.0.4) for about 5 days to build a mini HTPC, and that side of things is going relatively well. Ubuntu, however, is baffling my fragile little mind (softened by years of windows abuse etc).

Most prominent in my teething problems is that whenever I perform any kind of install operation (eg synaptic), or do something in terminal, I frequently get some kind of lirc error with it. It usually lists 3 or 4 lirc associated bits and bobs, something like gnome lirc, lirc, mythbuntu lirc etc.

So for example last night I was tinkering with Flash plugins (because apparently youtube and ubuntu hate each other) and whenever I added/removed stuff it often came with a lirc error, even though there really isn't any relation. Usually the adding/removing was successful and the lirc error didn't affect it but it's pretty annoying/worrying.

Obviously I could add and remove lirc but I'm not convinced that's a good idea seeing as installation didn't go very smoothly, although I am less of a noob now. Any input would be appreciated...as would a miracle cure for iplayer and youtube not working.

(I'm running Asrock Ion 330, Intel Atom 1.6ghz, 2gb RAM and ION chipset)

Cheers! Apologies if this is in wrong place/answered repeatedly/insert other enormous faux pas here

---

### Post by Hospadar on 2009-09-01
We really can only help if you post the exact error messages you get and what you did to cause them.

It's probably a pretty simple problem other than that.

---

### Post by LowSky on 2009-09-01
copy and paste the issue into a reply so we know exacly LIRC should be comming up as an error when you install unrelated software

LIRC is for remote control management, so it has no effect on Flash installtion

---

### Post by panasonicyouth on 2009-09-01
Thanks for replies - yeah figured that might help but was on vista laptop at the time!

So for example I just thought I'd add 7zip in the Add/Remove window. Got "an error occurred" and the following in said new window:

E: lirc: subprocess post-installation script returned error exit status 127
E: gnome-lirc-properties: dependency problems - leaving unconfigured
E: mythbuntu-lirc-generator: dependency problems - leaving unconfigured
E: lirc-x: dependency problems - leaving unconfigured

When I hit details to get terminal style command details up there is a whole truckload of gibberish about the above.

After I click out of that I am told that software was successfully installed.

:confused: Is rather strange!

---

### Post by panasonicyouth on 2009-09-04
Bump? Trying to uninstall Avant Window Manager now and it won't work because it grumbles about LIRC despite it being totally irrelevant.

---

### Post by oldos2er on 2009-09-04
Check Software Sources, and make sure you have the universe repository enabled.

---

### Post by panasonicyouth on 2009-09-06
Hmm it says it's enabled under Software Sources? Thanks for the suggestion either way...:(

---

