---
title: "Thunderbird instead of Evolution? Will notification still work via mail icon?"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-06-03
I was wondering about switching to Thunderbird instead of using Evolution for my mail, but will I still be able to check my mail using the mail icon in the panel at the top which has access to Broadcast and Pidgin?

---

### Post by Autodave on 2010-06-03
> **UnknownFear said:**
> I was wondering about switching to Thunderbird instead of using Evolution for my mail, but will I still be able to check my mail using the mail icon in the panel at the top which has access to Broadcast and Pidgin?

Thunderbird will create an icon in the Applications > Internet menu which you can then drag to the top menu bar.

---

### Post by ubunterooster on 2010-06-03
Not without a good bit of programing, I don't think will the default icon show Thunderbird ( That's the "Me Menu" )

Dave's will add an icon for Thunderbird, though

---

### Post by UnknownFear on 2010-06-03
> **Autodave said:**
> Thunderbird will create an icon in the Applications > Internet menu which you can then drag to the top menu bar.

lol, I know that. What I was wondering is if I can access my mail and everything from the same icon as Evolution is in with Broadcast.

---

### Post by UnknownFear on 2010-06-03
> **ubunterooster said:**
> Not without a good bit of programing, I don't think.

Ok, I'll just stick to Evolution for the time being. Thanks for the reply.

---

### Post by wombatvvv on 2010-06-03
further to the point, is there anyway of removing the Evolution icon *without* removing the sound-controller, battery and bluetooth icons? I am happy to use the Thunderbird icon instead, but if want to get rid of the evolution one, I can't seem to do it without also removing the sound controller and blue-tooth icon thing.

Is there some way maybe to put blue-tooth and sound up there individually, like the Thunderbird icon, without using the "Add to panel" option?

---

### Post by wombatvvv on 2010-06-03
I would hardly call this "solved" ...

---

### Post by ubunterooster on 2010-06-03
> **wombatvvv said:**
> further to the point, is there anyway of removing the Evolution icon *without* removing the sound-controller, battery and bluetooth icons?
They are all three only there as part of the "notification area" so no you cannot do that either. Supposing you could remove notification area and then add back bluetooth and sound, other, important notifications would also be gone. 

Sorry, by at least you _can_ mark threads as "unsolved" via same method used to mark it as solved

---

### Post by uRock on 2010-06-03
> **wombatvvv said:**
> I would hardly call this "solved" ...
Of course it is solved. The OP got his/her question answered.

---

### Post by jeremyswalker on 2010-06-03
Even though the default notification will not work, you could still get a similar effect. I use the Firetray extension. It keeps thunderbird in the notification area, and tells me when I get new messages (as well as how many I have).

[https://addons.mozilla.org/en-US/thunderbird/addon/4868/]("https://addons.mozilla.org/en-US/thunderbird/addon/4868/")

Note: If you are using 64-bit 10.04, you have to download from the authors site at [http://code.google.com/p/firetray/downloads/list]("http://code.google.com/p/firetray/downloads/list")

---

### Post by wombatvvv on 2010-06-03
> **jeremyswalker said:**
> Even though the default notification will not work, you could still get a similar effect. I use the Firetray extension. It keeps thunderbird in the notification area, and tells me when I get new messages (as well as how many I have).

[https://addons.mozilla.org/en-US/thunderbird/addon/4868/](https://addons.mozilla.org/en-US/thunderbird/addon/4868/)

Note: If you are using 64-bit 10.04, you have to download from the authors site at [http://code.google.com/p/firetray/downloads/list](http://code.google.com/p/firetray/downloads/list)

The main things I'm worried about are the battery, bluetooth, sound, etc. 

Really, evolution shouldn't be part of that little notification panel at all. I know it's a very minor thing really, bujt It's a bit Microsoft/Apple-ish to make an OS that has "in built features" that rely on one particular piece of software like that, and it's the reason I moved away from those options. Yeah I know, it's a small thing.

Where can I put a suggestion for the next version? :)

---

### Post by wombatvvv on 2010-06-03
> **uRock said:**
> Of course it is solved. The OP got his/her question answered.

Well I suppose that's fair enough if you don't mind "almost the same thing, but not quite" getting posted multiple times with each subtle variation. I thought it would be better to keep posting here instead of starting a new thread entitled: Thunderbird instead of Evolution? Will other notification icons still work once mail is removed?[]("http://ubuntuforums.org/showthread.php?t=1501050")

---

### Post by ubunterooster on 2010-06-03
> **wombatvvv said:**
> Will other notification icons still work once mail is removed?
Once Evolution mail is removed? No :(

---

### Post by J V on 2010-07-01
I did this... Unfortunately it won't let me take a screenie while the window is open... IIRC I needed to change some files in /etc but they were deep and I don't remember where, feel free to google :P

Edit: Yeah: /usr/share/indicators/messages/applications

---

### Post by auh2o on 2010-07-30
> **J V said:**
> I did this... Unfortunately it won't let me take a screenie while the window is open... IIRC I needed to change some files in /etc but they were deep and I don't remember where, feel free to google :P

Edit: Yeah: /usr/share/indicators/messages/applications

NOW it is solved! ("It can't be done" is NOT a solution.)

Shame nobody thanked you at the time, but let me sincerely thank you now! Was just wondering how to accomplish this, and it's great that there was such a simple solution.

---

