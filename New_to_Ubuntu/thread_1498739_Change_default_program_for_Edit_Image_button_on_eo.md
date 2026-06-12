---
title: "Change default program for Edit Image button on eog (Eye of Gnome) image viewer"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-01
When I view an image with eog (Eye of Gnome), I see a button "Edit Image".

The button takes me to F-Spot.

How can I change this to go to GIMP?

---

### Post by laidback on 2010-06-01
I think you require to change the default image viewer which can be done as follows:-

right click on image
choose Properties (last in list)
now select the Open with tab, 4th along
from the list presented choose which viewer/package to use when you click            on this type of file

You may need to set this preference again should you want to open a variety (different types of file, e.g. .png, .jpg etc) with your preferred application as I think the preference is applied individually to each type. So you could have .jpg with Eog and .png with FSpot etc. But you only need to set each type once.

In case there is a difference I'm using v9.04, you're on 10.04 I believe.

---

### Post by Paddy Landau on 2010-06-01
Thanks, but that's not quite what I'm after.

I want eog to remain the default application for viewing images. What I want changed is the "Edit Image" button when I have eog open.

I'm not sure if 9.04 has that option. See the screenshot of the button.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=159007&stc=1&d=1275389414[/IMG]

---

### Post by laidback on 2010-06-01
No it doesn't, all I get is the Edit button with no options.

---

### Post by laidback on 2010-06-01
I've just loaded my trial 10.04 version and see what you mean. Nice touch that button. I suspect that there is a setting somewhere in the hidden directory for Eog but I've had a quick look in mine (~/.eog) and couldn't see anything obvious. Perhaps a search on the web for Eog might help.

---

### Post by laidback on 2010-06-01
Looking in /usr/share/eog doesn't produce anything obvious either.

---

### Post by Paddy Landau on 2010-06-01
> **laidback said:**
> I suspect that there is a setting somewhere in the hidden directory for Eog but I've had a quick look in mine (~/.eog) and couldn't see anything obvious. Perhaps a search on the web for Eog might help.
I have Googled but come up with nothing. The help and the eog website both give no clue.

I suspect that it's built into the program, rather than as a parameter, which would be a pity.

BTW, the directory is ~/.gnome2/eog. Nothing there refers to f-spot.

I wonder where I could file a change request?

---

### Post by philinux on 2010-06-01
I've no edit image button as I've replaced f-spot with gthumb.

From eog I use File>Open With

---

### Post by Paddy Landau on 2010-06-01
> **philinux said:**
> From eog I use File>Open With
Oh, that's a good workaround, thanks.

---

### Post by philinux on 2010-06-01
> **Paddy Landau said:**
> Oh, that's a good workaround, thanks.

Or you could mess around here. Replace with gimp.desktop  Not sure if it will work.

---

### Post by laidback on 2010-06-01
Have a look at "Help" > "Get help online.." I don't expect you will find an answer but you can also ask a question, which might enable you to make a request.

---

### Post by Paddy Landau on 2010-06-01
> **philinux said:**
> Or you could mess around here...
Thanks for the idea. Sadly, EOG didn't like gimp.desktop.

---

### Post by Paddy Landau on 2010-06-01
> **laidback said:**
> Have a look at "Help" > "Get help online.." I don't expect you will find an answer but you can also ask a question, which might enable you to make a request.
Great idea! Having failed with Google, I've asked [this question]("https://answers.launchpad.net/ubuntu/+source/eog/+question/113149").

---

### Post by philinux on 2010-06-01
> **Paddy Landau said:**
> Great idea! Having failed with Google, I've asked [this question]("").

Well for certain f-spot will be replaced by shotwell in Maverick.

---

### Post by Paddy Landau on 2010-06-03
Bizarre this is!

[Phil suggested]("http://ubuntuforums.org/showthread.php?p=9393665#post9393665") that I change the setting in gconf-editor, and that didn't work for me.

My [question on Launchpad]("https://answers.launchpad.net/ubuntu/+source/eog/+question/113149") gave the same answer.

So, I tried again, and this time it worked.

I guess that I mistyped the first time.

Thank you Phil and Launchpad for the answer!

---

