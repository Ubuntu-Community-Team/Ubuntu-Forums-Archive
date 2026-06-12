---
title: "Importing bookmarks from firefox &amp; chrome in windows"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Davy49 on 2010-10-23
Hi,
As I'm still rather new to the ubuntu/linux system, I'm still having some difficulties getting some things accomplished. The most recent of which is getting my saved bookmarks that I use in windows 7 imported over into the firefox & google chrome browser in ubuntu. I've read about different ways to get this done, but so far I haven't got it to work. I've saved the respective bookmarks from both browsers onto my usb flash drive, thinking it would be easy just to import them directly from the flash drive, but so far It hasn't worked. In windows I'm used to just opening up windows explorer, and working with files in there. In ubuntu, there isn't a similar area, or at least if there is...I don't know about it. The more I learn about ubuntu, there more I seem to like it.Thanks for any help that might be offered.
David :(

---

### Post by howefield on 2010-10-23
You could use the synchronisation feature in Chrome or to import the bookmarks file, go to Options > Bookmark Manager > Organise > Import Bookmarks.

Can't quite remember Firefox, but it the option to import is in the Bookmark > Organise Bookmarks > Import and Backup.

Have you tried these methods and not worked ?

---

### Post by Davy49 on 2010-10-23
Hi,
Thanks for a quick reply, as I remember I've already tried the methods you mentioned. As I previously stated, I thought this would be an easy task by having saved my bookmarks I use in windows 7 copied onto my usb flash drive.
Thanks,
David

---

### Post by Pconfig on 2010-10-23
Did you also try the build in sync function in chrome?
In firefox you can install [https://addons.mozilla.org/en-US/firefox/addon/10868/](https://addons.mozilla.org/en-US/firefox/addon/10868/) to keep your bookmarks and history synchronized

---

### Post by howefield on 2010-10-23
> **Davy49 said:**
> I thought this would be an easy task by having saved my bookmarks I use in windows 7 copied onto my usb flash drive.

It is an easy task if you export your bookmarks as an html file to your USB flash.

If you have copied them from your windows install using the file manager, then life is a bit more difficult.

---

### Post by lovinglinux on 2010-10-23
Do you have a single html file with all your bookmarks or do you have a bunch of icons on your desktop that link to individual pages?

The equivalent of Windows Explorer in Ubuntu is called Nautilus file browser. You can open the file browser from the places menu.

---

### Post by Davy49 on 2010-10-23
Thanks for the replies..as far as the firefox html file, all of my bookmarks that I use in the windows firefox side are contained in one html file. As far as the google chrome browser goes,the bookmark folder in that browser is a bak file. I never would have thought it would have been so difficult for me to get these bookmarks imported.
David :(

---

### Post by lovinglinux on 2010-10-23
> **Davy49 said:**
> Thanks for the replies..as far as the firefox html file, all of my bookmarks that I use in the windows firefox side are contained in one html file. As far as the google chrome browser goes,the bookmark folder in that browser is a bak file. I never would have thought it would have been so difficult for me to get these bookmarks imported.
David :(

First of all check if your bookmark html file from the Windows side really has bookmarks in it. If you have copied the file **bookmarks.html** from the Firefox profile in Windows, then you are doing it wrong. That file is no longer used. The bookmarks are currently stored in the file **places.sqlite**. So to migrate your bookmarks from the Windows side to the Ubuntu side, all you need is to copy the **places.sqlite** file from one to another. If your bookmarks.html was exported from Firefox and it does have bookmarks in it, then all you need is to import them back into the Ubuntu Firefox, using the Bookmarks Manager. 

I don't use Chrome and not sure if you have the correct file format.

---

### Post by Davy49 on 2010-10-24
Dear lovinglinux,
Thanks SO much for trying to supply me with the info. I need to solve my little problem. As far as my firefox bookmarks are concerned..while looking in my firefox profile folder, I see this file: urlclassifier3.sqlite , but I didn't see this file places.sqlite , as you mentioned in your previous post. The file I mentioned in my profile folder ( urlclassifier3.sqlite ) is 36,164 KB in size. However...upon further discovery, I did find the sqlite file in a different folder in my user/app.data/roaming folder, while the previous file I mentioned ( urlclassifier3.sqlite ) is in the user/app.data/local folder...hmmmmm is that 'normal' ? I fully intend to get this little ' hiccup on my ubuntu road resolved one way or another. At least for me, I find myself using the google chrome browser more than any other browser. Have a GREAT day !!
David :)

---

### Post by lovinglinux on 2010-10-24
> **Davy49 said:**
> Dear lovinglinux,
Thanks SO much for trying to supply me with the info. I need to solve my little problem. As far as my firefox bookmarks are concerned..while looking in my firefox profile folder, I see this file: urlclassifier3.sqlite , but I didn't see this file places.sqlite , as you mentioned in your previous post. The file I mentioned in my profile folder ( urlclassifier3.sqlite ) is 36,164 KB in size. However...upon further discovery, I did find the sqlite file in a different folder in my user/app.data/roaming folder, while the previous file I mentioned ( urlclassifier3.sqlite ) is in the user/app.data/local folder...hmmmmm is that 'normal' ? I fully intend to get this little ' hiccup on my ubuntu road resolved one way or another. At least for me, I find myself using the google chrome browser more than any other browser. Have a GREAT day !!
David :)

I think that is normal with Windows. Just try to use that places.sqlite. The urlclassifier3.sqlite is not what you need.

---

### Post by ArgusVision on 2010-10-24
You could also look at Ubuntu One to sync your files/browser/contacts etc.
There is a beta windows client that I haven't tried out yet. That could keep you insync which ever OS or browser you're using.

Check out [http://one.ubuntu.com](http://one.ubuntu.com)

---

### Post by farsight on 2010-10-24
Hey,

If you are trying to sync bookmarks, maybe you could try Xmarks (an addon for firefox). I believe it works with a range of browsers, you simple need to register a username and password. It's something I'm currently testing, so thought I'd at least let you know there is a simple way to sync if you are having trouble :)

Best of luck
Farsight

---

### Post by lovinglinux on 2010-10-24
> **ArgusVision said:**
> You could also look at Ubuntu One to sync your files/browser/contacts etc.
There is a beta windows client that I haven't tried out yet. That could keep you insync which ever OS or browser you're using.

Check out [http://one.ubuntu.com](http://one.ubuntu.com)

I haven't use it yet, but the Ubuntu One page says "Sync Tomboy notes and Firefox bookmarks with your personal cloud". So does it really sync with other browsers?

---

### Post by farsight on 2010-10-24
Hey again,

I am not sure if Ubuntuone works with windows at the moment, I know I certainly had difficulties several months ago and so had to find a different sync method when I was organising group work.

Syncing the Tomboy notes and bookmarks to Ubuntuone (to my knowledge) would allow you to transfer and backup bookmarks and Tomboy notes between Ubuntu systems, but not between Ubuntu and Windows.

---

### Post by lovinglinux on 2010-10-24
> **farsight said:**
> Hey again,

I am not sure if Ubuntuone works with windows at the moment, I know I certainly had difficulties several months ago and so had to find a different sync method when I was organising group work.

Syncing the Tomboy notes and bookmarks to Ubuntuone (to my knowledge) would allow you to transfer and backup bookmarks and Tomboy notes between Ubuntu systems, but not between Ubuntu and Windows.

What about other browsers in Ubuntu systems, like Chrome and Opera? I don't think they can be sync'd because otherwise this would come up in other threads when Xmarks announced they were closing.

---

### Post by howefield on 2010-10-24
> **lovinglinux said:**
> this would come up in other threads when Xmarks announced they were closing.

Offtopic :
Lest others think they are closing for sure, it isn't certain that this will be the case. A sale is being confidently touted.

Now back to the thread.

---

### Post by Davy49 on 2010-10-24
Thanks, I'll try your suggestion.
David

---

### Post by SuaSwe on 2010-10-24
> **howefield said:**
> 
A sale is being confidently touted


Gawd, I hope so! Xmarks is just awesome. Would highly recommend it to the OP also. :) 

Pretty sure Chrome bookmarks are also stored in a .html file - did you try going to the bookmark manager, do Tools > Export and save that file?

---

### Post by ArgusVision on 2010-10-25
Lovinglinux, (Battlestar Galactica fan?)

     I'm fairly certain chrome on linux keeps it's bookmarks in a folder like the rest of the browsers. It may not sync directly like firefox, but if you sync chrome's folder it should work. As far as IE goes... I might have over generalized with that one... but you could possibly sync the folder somewhere in the wine architecture.. Or just ignore IE, and port the book marks into firefox like everyone else. :)

---

### Post by lovinglinux on 2010-10-25
> **ArgusVision said:**
> Lovinglinux, (Battlestar Galactica fan?)

Yep, best series ever.





<<< see my location :)

---

### Post by ArgusVision on 2010-10-25
I noticed. I'm kind of a Lord of the BattleStar-Trek Wars & Dragons hybrid Geek myself... But we'd better get back on topic before we're Cafe-ed or worse...

I know, my fault... I started it.

---

### Post by Davy49 on 2010-10-27
Well, some good news..I did in fact get my google chrome bookmarks imported into my ubuntu google chrome browser. It sure makes things a lot better, I use the chrome browser more now than firefox, I just like it better. Thanks again for the help.
David :)

---

