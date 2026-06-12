---
title: "Opening notepad .txt document in Ubuntu."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by calderp on 2009-01-24
I'm trying to open a rather important .txt file that is from when I had Vista installed and it won't open with gedit. My other .txt files from the same directory open fine though. Is there another program I can use to try and recover the file?

I am getting this error:

Could not open the file /home/calderp/Desktop/Do two of these per day.txt.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.


THe character coding it is trying to use is Current Locale (UTF-8 )

Any ideas?

---

### Post by taurus on 2009-01-24
What's the output of this command from a terminal?

```
file /home/calderp/Desktop/"Do two of these per day.txt"
```
Otherwise, see if you can even view it with more.

```
more ~/Desktop/"Do two of these per day.txt"
```

---

### Post by calderp on 2009-01-24
Sorry, was out for a bit. No luck with more, and it appears to be an ACB file, whatever that is...?

```
calderp@paulpc:~$ file /home/calderp/Desktop/"Do two of these per day.txt"
/home/calderp/Desktop/Do two of these per day.txt: ACB archive data
calderp@paulpc:~$ more ~/Desktop/"Do two of these per day.txt"



calderp@paulpc:~$ 

```

---

### Post by taurus on 2009-01-24
[http://www.file-extensions.org/acb-file-extension-aol-cab-launcher](http://www.file-extensions.org/acb-file-extension-aol-cab-launcher)

---

### Post by calderp on 2009-01-24
Huh, that's really weird... It's definitely a txt file that I made with Notepad... Any idea how it might have gotten to be an ACB or how I might be able to recover / open it? Is it a lost cause?
Thanks for the help

---

### Post by handydan918 on 2009-01-24
If you use AOL and Windows....
yeah.

---

### Post by calderp on 2009-01-24
Well, I've never had anything related to AOL installed on anything, and this file was never opened or edited with anything other than Notepad, so I have no freaking clue how/why it would be showing up as this.

---

### Post by SunnyRabbiera on 2009-01-24
You could try to cheat, by right clicking the file and just trying to label it as a .txt

---

### Post by taurus on 2009-01-24
Or you could try installing wine since it comes with a notepad.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by teh_yodeler on 2009-01-25
I like the wine idea.

---

### Post by Hobgoblin on 2009-01-25
Sounds like it is either corrupted or is not a plain text file.

---

### Post by The Cog on 2009-01-25
You could try looking at the start of the file with a hex editor to see what's really there. try this:
> sudo aptitude install ghex
ghex2 'Do two of these per day.txt'
and post a screenshot

---

### Post by Tomatz on 2009-01-25
Try opening it with open office ;)

---

### Post by calderp on 2009-01-25
Hi All, 
thanks for all the suggestions. I have tried:
opening with wine notepad - no luck
renaming as .txt and opening with gedit - no luck
opening with openoffice - no luck

Here is the screenshot of ghex. If this doesn't provide anything useful, I guess I'm ready to give up.
[http://picasaweb.google.com/lh/photo/8hL_mmqAvl0h0936X1ycww?feat=directlink]("http://picasaweb.google.com/lh/photo/8hL_mmqAvl0h0936X1ycww?feat=directlink")

---

### Post by SunnyRabbiera on 2009-01-25
> **calderp said:**
> Hi All, 
thanks for all the suggestions. I have tried:
opening with wine notepad - no luck
renaming as .txt and opening with gedit - no luck
opening with openoffice - no luck

Here is the screenshot of ghex. If this doesn't provide anything useful, I guess I'm ready to give up.
[http://picasaweb.google.com/lh/photo/8hL_mmqAvl0h0936X1ycww?feat=directlink]("http://picasaweb.google.com/lh/photo/8hL_mmqAvl0h0936X1ycww?feat=directlink")

I would just give up, and make sure next time notepad on windows saves it right.

---

### Post by Tomatz on 2009-01-25
If the .txt is not too private. You can attach it to your next post so we could try to open it?

Just click "new reply", then click the paperclip ;)

---

### Post by calderp on 2009-01-25
> **Tomatz said:**
> If the .txt is not too private. You can attach it to your next post so we could try to open it?

Just click "new reply", then click the paperclip ;)

Sure, it's just a to-do list, but it's from a while ago, and my brain is very scattered, and I'm afraid I'll forget something relatively important...

---

### Post by SunnyRabbiera on 2009-01-25
> **calderp said:**
> Sure, it's just a to-do list, but it's from a while ago, and my brain is very scattered, and I'm afraid I'll forget something relatively important...

Yeh it looks like a bad file, its all gibberish here

---

### Post by Tomatz on 2009-01-25
> **SunnyRabbiera said:**
> Yeh it looks like a bad file, its all gibberish here

Same here :( 

I will try to open it in xp soon.

---

### Post by calderp on 2009-01-25
Huh. Very weird, I have no idea how that could have happened, but I guess that's the way of computers. If you want to try it in XP that would be helpful but if it doesn't work, I'm ready to call it quits. Thanks so much for all of your help.

Oh, and while I'm posting I have a quick question if anyone knows? I'm used to the backspace key working as a back button in Mozilla but it doesn't do that for me in Ubuntu. Do you know if that's a setting I can change? I couldn't find anything in preferences.

---

### Post by llamabr on 2009-01-25
I'm afraid that notepad in xp is not going to open it either, because it's not a text file.  'acb' is some archive owned by aol.  You'll need their own proprietary software to open it.

If you really do want to make text to do lists in notepad, make sure to save them as ascii text.

The backspace thing was a workaround to fix a bug.  You can resurrect it here:

[http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/](http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/)

---

### Post by calderp on 2009-01-25
Well, I guess that's that. Thanks all for your help!

---

### Post by toberc on 2009-07-15
Hi, many of you seem to know a few things about notepad. I was wondering if you could help me with my problem. Here is a link to my thread!
 
[[COLOR=#000000]Insert a linked object from an Excel file into a Text (csv) file[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1213677&highlight=linked+object") 
 
Thank you!

---

