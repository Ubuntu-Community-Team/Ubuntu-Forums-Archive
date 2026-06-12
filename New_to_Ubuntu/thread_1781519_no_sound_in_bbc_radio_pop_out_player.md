---
title: "no sound in bbc radio pop out player"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2011-06-13
Hi All,
I followed a 2010 thread to solve this, but to no avail. I can watch and listen to anything on the bbc website except when it uses its pop out player. Then the graphics move as if it is playing, but no sound comes out. Following advice on the other thread I logged in as a guest and hey presto, it worked. I assume this means it is nothing to do with my browser or sound system, but something in the set up of my personal log in. Any advice in the computer equivalent of words of one syllable greatly appreciated.
Thanks.

---

### Post by wolfen69 on 2011-06-13
Rename your ~/.mozilla file to .mozilla_backup or something. Then restart firefox.

---

### Post by Dermot Doyle on 2011-06-13
Hi, where do I find that file?
Thanks

---

### Post by ajgreeny on 2011-06-13
The new radio player is a ridiculous thing, using flash instead of a more sensible stream, and I am also having trouble with it, but as it is flash, I prefer not to use it anyway.

I tend to use the media streams listed at  [http://bbcstreams.com/](http://bbcstreams.com/)  which will work in a standard media player plugin, or can be saved to the bookmarks of Radio Tray (available from the repos).

PS:
I forgot to say that if you go to the home page for the radio station eg BBC Radio3 at [www.bbc.co.uk/radio3](www.bbc.co.uk/radio3) there is a **listen live in HD** button top right;  still uses flash, but it does work, which is more than can be said for the pop-up radio player!.

---

### Post by Dermot Doyle on 2011-06-15
Yes I can listen to the current programmes, but I like to listen again or to things I have missed so I still want to get the pop out player working. I can't believe it is beyond the wit of Ubuntu man to get the sound from something that is clearly playing. 
Wolfen69 (or anyone), can you tell me where to find the mozilla file you mentioned?
Cheers

---

### Post by Dermot Doyle on 2011-07-13
Hi, still no nearer to solving this one. Any ideas?
Cheers

---

### Post by John Peschken on 2011-07-13
Okay, I'm new with this and not near my Ubuntu computer right now, so take this with a grain of salt.  
 
I believe ~/.mozilla should be a hidden folder in the root directory.  "~" means root, "." means hidden. 
 
As I recall. Ctrl-H should unhide or re-hide hidden files or folders if you can't see it.

---

### Post by Swagman on 2011-07-13
I just had a play around a found the pop out player...

[[IMG]http://img94.imageshack.us/img94/6546/bbcr2.th.png[/IMG]](http://img94.imageshack.us/i/bbcr2.png/)

Web address I found it on was ... [http://www.bbc.co.uk/programmes/b007xvtd](http://www.bbc.co.uk/programmes/b007xvtd) <--- click that orange  button top right opens pop out player

pop out player for R2

[http://www.bbc.co.uk/iplayer/console/bbc_radio_two](http://www.bbc.co.uk/iplayer/console/bbc_radio_two)

---

### Post by CatKiller on 2011-07-13
> **John Peschken said:**
> I believe ~/.mozilla should be a hidden folder in the root directory.  "~" means root, "." means hidden. 
 

~ means "this user's Home directory." You're right that files beginning with a . are hidden by default.

---

### Post by Dermot Doyle on 2011-07-14
Thanks for the replies. Now, when I try to open the root folder to find the hidden file it says I don't have permission to open it. So how do I give myself permission?

---

### Post by Swagman on 2011-07-14
alt + F2

enter gksudo nautilus

You now have the power to royally stuff your system

be careful

---

### Post by Dermot Doyle on 2011-07-14
Hi Swagman, I did what you said, and used Ctrl H to see the hidden folders, but couldn't find any folder named .mozilla. Looking back through the thread I realise that CatKiller said the symbol meant the user's Home Directory, but I can't find anything in the home folder either (if that is where I should be looking).
Can I say that all this welcome advice assumes that Wolfen69 was right about renaming a folder to solve the problem. Do you think that is right, because there's no point in me spending time getting into parts of the computer better left alone if his idea won't work?
Cheers

---

### Post by Swagman on 2011-07-14
Ok .. Just read the entire thread so I cn get a gist of where we are.

You **DO NOT** need root (sudo) power so close that gksudo nautilus window.

**YOU** are the owner of anything in your **/Home** folder and as such you don't need root privileges.

here's a screengrab of the .mozilla folder in my /Home 

[img]http://img24.imageshack.us/img24/1526/mozillaprefs.jpg[/img]

so.. Click Places and then view hidden files (ctrl + h) scroll down below folders and you will see the . folders

The . means hidden (prefs)

You are runnng Firefox so you **WILL** find that .mozilla folder there !!

Rename it something like .BAKmozilla so you are not actually deleting it. if something goes wrong you can simply rename it back again.

Try that

---

### Post by Dermot Doyle on 2011-07-14
Hi All, for what it's worth I seem to have fixed the problem. I had the flash player blocker enabled (I think) and only pressed play to listen to the radio, which didn't work as I said. This time I right-clicked on the player and allowed flash player for that site and hey presto it worked straight off. Turning it off and trying another it opened and played no problem. I am probably less computerate than people realise and made a more simple mistake than anyone guessed.
Cheers

---

### Post by Swagman on 2011-07-14
No worries..

When all else fails.. Try the simple stuff !!

hehe

I'm glad you got it sorted

---

### Post by brumman on 2013-02-12
> **ajgreeny said:**
> The new radio player is a ridiculous thing, using flash instead of a more sensible stream, and I am also having trouble with it, but as it is flash, I prefer not to use it anyway.

I tend to use the media streams listed at  [http://bbcstreams.com/](http://bbcstreams.com/)  which will work in a standard media player plugin, or can be saved to the bookmarks of Radio Tray (available from the repos).

PS:
I forgot to say that if you go to the home page for the radio station eg BBC Radio3 at [www.bbc.co.uk/radio3]("http://www.bbc.co.uk/radio3") there is a **listen live in HD** button top right;  still uses flash, but it does work, which is more than can be said for the pop-up radio player!.

At feb 12 2013 the pop-up radio player does NOT work for any stations live streaming and your  **listen live in HD **button does not exist!
I think all "listen again" programs do work - just live feeds which have the problem.
This could be a problem with Firefox 18 though because on Windows you get the same issue with local radio, however ALL stations, live and recorded, work flawlessly in IE! 

Now using the alternative media streams, for example
 *[http://bbc.co.uk/radio/listen/live/bbcwm.asx](http://bbc.co.uk/radio/listen/live/bbcwm.asx)        *then in FF18 on Win7 the local radio streams will play live, However in Ubuntu 12.04 Firefox doesn't recognise the asx extension even with the WMP plug-in installed.
Guess I'll just have to continue using Windows and IE for some stations! Ugh.
The BBC seem to have no clue about this and it would be useful in my discourse with them if I can show this as a common problem, so please if you are experiencing the same issue please indicate.

---

### Post by nothingspecial on 2013-02-12
It is still possible to listen to those stream urls in external applications such as radiotray, vlc, mplayer etc.

---

### Post by brumman on 2013-02-12
> **nothingspecial said:**
> It is still possible to listen to those stream urls in external applications such as radiotray, vlc, mplayer etc.
   Yes you are right! I've just got all the BBC streams playing in Rhythmbox - now why couldn't the IT experts at BBC explain that!
Here's a great link: 
Add BBC Internet radio Stations to Rhythmbox in Ubuntu 12.04
[http://dnpashilkar.wordpress.com/2012/05/14/add_bbc_internet_radio_stations_rhythmbox_ubuntu/](http://dnpashilkar.wordpress.com/2012/05/14/add_bbc_internet_radio_stations_rhythmbox_ubuntu/)

---

### Post by aka-John99 on 2013-02-12
> **wolfen69 said:**
> Rename your ~/.mozilla file to .mozilla_backup or something. Then restart firefox.
Maybe it would have been as easy to just start Firefox in safe-mode. Hold the shift key whilst launching Firefox, but do NOT use the reset option. 

Firefox also has a **reset** option from safe mode, but I agree  renaming .*mozilla* is a better option if that is being considered.  (Until recently there were several individual reset options but they are no longer available from the GUI) Reset removes all add-ons amongst other things.

Another method  of forcing a new profile creation is renaming  the file *profiles.ini   *that will create another new *xxxxxxxx.default *profile. (The pseudo random string xxxxxxxx will differ.)

---

### Post by Ian_M._Stewart on 2013-10-15
> **ajgreeny said:**
> 
I tend to use the media streams listed at  [http://bbcstreams.com/](http://bbcstreams.com/)  which will work in a standard media player plugin, or can be saved to the bookmarks of Radio Tray (available from the repos).


HOORAY!  Thanks very much ajgreeny.  I was looking for a sensible way to listen to the BBC without all htat flash/website nonsense.  Your post was a saver for me.:biggrin:\\:D/

---

### Post by Buntu Bunny on 2013-10-15
> **Dermot Doyle said:**
>  ... (or anyone), can you tell me where to find the mozilla file you mentioned?

It's in your home folder, but it's hidden. 

View menu > show hidden files

Any time you see a file name beginning with a dot, as in .mozilla, look for it as a hidden file in your home folder (home > Dermot Doyle).

---

