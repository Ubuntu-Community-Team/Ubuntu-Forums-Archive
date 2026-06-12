---
title: "How do I set up my keyboard?"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by nussy on 2010-04-05
I cannot set up email because I get a " mark instead of @ on top of the 2 key.  I tried to change keyboard settings to no avail. 

My hard drive has folders that I created with Windows XP. How do I find them when I log in with Ubuntu? 

Im slow and frustrated.

---

### Post by Penguin Guy on 2010-04-05
I assume you have a standard UK keyboard but are using a US layout. To fix this, click [COLOR="Green"]System -> Preferences -> Keyboard[/COLOR], then click the [COLOR="Green"]Layouts[/COLOR] tab. Click [COLOR="Green"]Add...[/COLOR] and choose [COLOR="Green"]Country: United Kingdom[/COLOR], [COLOR="Green"]Variants: United Kingdom[/COLOR], click [COLOR="Green"]Add[/COLOR] and select the new layout. Type some stuff in the test box and if everything works fine then click [COLOR="Green"]Apply System-Wide...[/COLOR]. Done.

EDIT: Obviously if you have a US keyboard, do the above steps, but replace UK with US.

---

### Post by durand on 2010-04-05
As for the second question, you can just go to Places > Computer. One of the drives there will be WinXP's, if you just double click on it, you should be able to find your files.

---

### Post by r-senior on 2010-04-05
> **Penguin Guy said:**
> I assume you have a standard UK keyboard but are using a US layout.
Other way around I think - using a UK/Euro layout on a US keyboard. OP gets " above the 2 but wants it to be @.

Quick workaround, and in no way a fix, is to press the " over on the RHS of the keyboard, which will probably give the @.

---

### Post by nussy on 2010-04-05
I am using A Microsoft Keyboard, Im In Canada 
Quick workaround, and in no way a fix, is to press the " over on the RHS of the keyboard, which will probably give the @. 	  	3 Hours Ago 12:21 PM

what does RHS mean......Thanks.  Still getting an "

---

### Post by durand on 2010-04-05
So did you change your keyboard layout to the canadian one? RHS means right hand side.

---

### Post by nussy on 2010-04-05
> **durand said:**
> So did you change your keyboard layout to the canadian one? RHS means right hand side.

I did change to Canadian...an the RHS key is the same......"

---

### Post by durand on 2010-04-05
Hmm, strange. The canadian layout is attached to this post. Are you sure that your keyboard matches up with that one? There don't seem to be any reported bugs about it. If you still think this is wrong, then the best thing is to probably report a bug, just press Alt+F2, and type in "ubuntu-bug gnome-keyboard-properties", then Enter, and follow the instructions.

---

### Post by nussy on 2010-04-05
> **durand said:**
> Hmm, strange. The canadian layout is attached to this post. Are you sure that your keyboard matches up with that one? There don't seem to be any reported bugs about it. If you still think this is wrong, then the best thing is to probably report a bug, just press Alt+F2, and type in "ubuntu-bug gnome-keyboard-properties", then Enter, and follow the instructions.
@

To solve the problem I just pasted the @ the appropraie place and it works just fine.

Thanks for bearing with me....
One more question 

How do I make the sound work. Cant hear

---

### Post by durand on 2010-04-05
Uhm.. That is quite a wide ranging question. You should open a new thread for that as I'm not too sure. Sorry :( One thing that might work is this:

Open a terminal (Applications > Accessories > Terminal).
Type in "alsamixer -c0"
You should get a window that looks like the one in the attached file. If you then press the left and right buttons to selet particular mixers, then m to unmute them and up and down to change the volume, you should hopefully get sound working. Ubuntu isn't usually this difficult, I think you might just be a bit unlucky with hardware :(

---

### Post by nussy on 2010-04-06
I have the Canada layout checked off. I have the proper keyboard name and model checked off. But I still get ". So I gave  up trying. 
I got everything else to work properly including sound. The email cant work untill the problem is solved.

---

### Post by durand on 2010-04-06
Just a thought, is the right layout at the top of the window? If it isn't, then it isn't being used as the default.

---

### Post by nussy on 2010-04-07
Yes Its on top of the window. It shall be resolved one way or the other. :lolflag:

---

### Post by nussy on 2010-04-08
> **nussy said:**
> Yes Its on top of the window. It shall be resolved one way or the other. :lolflag:

I installed another keyboard and it did not fix the problem so its not a hardware problem.

I was thinking of uninstalling Ubuntu (wubi) and starting over again. 

Not sure I can uninstal did not look into it yet.

---

### Post by durand on 2010-04-08
Uhm, if it's wubi, you can just use add/remove programs to uninstall, I think.

---

