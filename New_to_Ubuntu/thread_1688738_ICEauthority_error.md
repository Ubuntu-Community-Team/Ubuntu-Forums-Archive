---
title: "ICEauthority error"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by texstar420 on 2011-02-15
Ok all I did before this happened is change something in the login preferences to automatically and now I get: could not update ICEauthority file/ home/ yardeischb/ .ICEauthority. then I get 2 more errors after that. I have a feeling if I just change my setting for logging on automatically then this will go away. 

I need some help to fix this can anybody offer some guidance. I have look around for a solution but couldn't find anything in noob terms.
Thanks in advance.

---

### Post by Old *ix Geek on 2011-02-15
> **texstar420 said:**
> now I get: could not update ICEauthority file /home/yardeischb/.ICEauthorityDoes that file actually exist? If it does, you can try this:
```
chmod 777 ~/.ICEauthority; chmod 1777 /tmp
```
or this:
```
rm ~/.ICEauthority
```

(Obviously you need to log in and go to a terminal.)

After issuing either of the above commands, log out and log back in. Are things normal now? If not, the permissions on your home directory may have gotten screwed up, and changing them back to what they should be ought to solve the problem. Post again if necessary!

---

### Post by texstar420 on 2011-02-15
> **Old *ix Geek said:**
> Does that file actually exist? If it does, you can try this:
```
chmod 777 ~/.ICEauthority; chmod 1777 /tmp
```
or this:
```
rm ~/.ICEauthority
```

(Obviously you need to log in and go to a terminal.)

After issuing either of the above commands, log out and log back in. Are things normal now? If not, the permissions on your home directory may have gotten screwed up, and changing them back to what they should be ought to solve the problem. Post again if necessary!
Ok so because when I log in I get the errors I have to do the whole recovery method then enter in your commands at the root shell? Sorry if I'm not calling things the right name hope you understand wha I mean. Thanks

---

### Post by Old *ix Geek on 2011-02-15
> **texstar420 said:**
> Ok so because when I log in I get the errors I have to do the whole recovery method then enter in your commands at the root shell? Sorry if I'm not calling things the right name hope you understand wha I mean. ThanksIt's okay. :) No, there's NO NEED to do any kind of recovery/reinstall thing here. I should have been more explicit. Press [ctrl][alt][f1] to go to a console login screen; log in there and then type the commands I gave before. To log out from the console type **exit** and hit [enter]. To go back to your messed up GUI, press [ctrl][alt][f7] and log out (if that's possible--if not, you may have to do a hard reset). Now try logging back in as normal and see what happens.

---

### Post by texstar420 on 2011-02-15
Old *ix Geek here is what worked for me: as soon as I got the ubuntu login screen I went into terminal and logged in
-then typed rm ~/.ICEauthority and then enter
-then exit-then logged in and it asked me for some key ring so I entered my password.
-went into system > administration> user and groups and changed password back to ask at log in.
-then I rebooted and all is well now! 

All this just cause I didn't want to type my password every time I log in? Is there a fix for this that won't send me down a rabbit whole. Please tell me yes and teach me cause for now I don't want to have to type my password every time I log in. I already have to type it every time I make a change. 
Thanks for all of your help and patience.

---

### Post by texstar420 on 2011-02-15
I am not sure how to mark this as solved yet but it is so thanks just had the above question. Oh yeah and while I am at it. Everytime I love in I get some mail notification thing that comes up. What is it wanting me to do. Let me know if you need me to be more specific.

---

### Post by Old *ix Geek on 2011-02-15
> **texstar420 said:**
> Old *ix Geek here is what worked for me: as soon as I got the ubuntu login screen I went into terminal and logged in
-then typed rm ~/.ICEauthority and then enter
-then exit-then logged in and it asked me for some key ring so I entered my password.
-went into system > administration> user and groups and changed password back to ask at log in.
-then I rebooted and all is well now!Yay! I'm glad it's all sorted out now.
> All this just cause I didn't want to type my password every time I log in? Is there a fix for this that won't send me down a rabbit whole. Please tell me yes and teach me cause for now I don't want to have to type my password every time I log in. I already have to type it every time I make a change.No, this DEFINITELY should not have happened just because you wanted to store your password. I use KDE so I really can't help you, but it should be an easy matter of changing your settings...you were just unlucky that this fluke--which I've seen happen to other people--happened to you.
> Thanks for all of your help and patience.You're very welcome. :)

PS To mark the thread solved, use the 'edit' button on your original post, then select 'go advanced' and then you can edit the title and put [SOLVED] at the beginning.

---

