---
title: "How can I install screensavers"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by wooly62 on 2009-07-19
Hi,
I'm a real novice with Ubuntu but would like to download 3rd party screensavers and 9obviously) install them. I can download ok, but I can't open them and i don't know how to add them to the list of available screensavers - can anyone provide simple and detailed instructions please?
Thanks,
Wooly

---

### Post by schwascore on 2009-07-20
It depends on what operating system / window manager the screensaver is created for.  Here is a quick Google search for linux screensavers:

[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Z6G&ei=7J9kSsPHMc-_tgfEjJ2yAg&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+screensavers&spell=1]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Z6G&ei=7J9kSsPHMc-_tgfEjJ2yAg&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+screensavers&spell=1")

To my knowledge it's not possible to install windows based screen savers in linux, but I could be wrong.

---

### Post by zzyzx1 on 2009-07-20
I am interested in this as well. I am trying to get my Ubuntu desktop in the kitchen to play slide show of pictures from a shared drive across my home network on a windows machine.

I can get to the shared drive easily, but need a program to play the slideshow in screensaver mode. Simple/inherent for windows... and there is a free progam. maybe under WINE..???

---

### Post by wooly62 on 2009-07-20
Thanks for the link, but I was looking for celeb type pics and can't find those on the google search (not for linux i mean). Can I convert files designed for windows?

---

### Post by CatKiller on 2009-07-20
> **zzyzx1 said:**
> I am trying to get my Ubuntu desktop in the kitchen to play slide show of pictures from a shared drive across my home network on a windows machine.

I'd imagine that you would want to use either the Slideshow or GLSlideshow screensavers, both of which should already be included. I believe they take images from ~/Pictures, if it contains images, or /usr/share/pixmaps, if it doesn't. Symlink the location of the pictures you want to see to (a sub-directory of) ~/Pictures and you should be golden.

EDIT: BTW (especially for the OP) one of the highest malware-infested sets of results were for searches for screensavers. Don't install some random "screensaver program" that you found on the Internet on Windows. It isn't safe.

---

### Post by llamabr on 2009-07-20
Wine is very rarely the correct answer.

Your screensaver that shipped with gnome already has a slideshow setting.  Find it under Settings > Screensaver.  It'll want you to put your pix in a default file, or you can tell it where to look.

---

### Post by zzyzx1 on 2009-07-20
OK, here is the path to My Pictures on shared Windows drive:
 /smb://blitz/blitz_a%20(e)/My%20Pictures as reported to me by network file browser.

I put this path in the personal-slideshow.desktop config file and it didnt work.
Per this command - 
Exec=slideshow --location=/path/to/your/Pictures_folder
Found here -> [U][Pictures]("http://ubuntuforums.org/showthread.php?t=488866")

[/U]Just comes up with a blank screen....[U]
[/U]

---

### Post by llamabr on 2009-07-20
> **zzyzx1 said:**
> OK, here is the path to My Pictures on shared Windows drive:
 /smb://blitz/blitz_a%20(e)/My%20Pictures as reported to me by network file browser.

I put this path in the personal-slideshow.desktop config file and it didnt work.
Per this command - 
Exec=slideshow --location=/path/to/your/Pictures_folder
Found here -> [U][Pictures]("http://ubuntuforums.org/showthread.php?t=488866")

[/U]Just comes up with a blank screen....[U]
[/U]
I'm not very good at samba, but I don't think that's what it's looking for.  Is the windows partition mounted?  What's the output of 
```
df
```
I think you're almost there, but you want an absolute path.

---

### Post by zzyzx1 on 2009-07-20
Yep, its mounted... i can get to it every other way... I think its the symlink piece that im missing...?

Im posting from a separate machine (since FF3.5 causes my CPU to overload on Ubuntu machine, another issue to attack)

What are you looking for in df? To much to re-type....

Thanks!

---

### Post by llamabr on 2009-07-20
Ya, eventually, you'll want to set up a symlink.

With df, I'm looking for where the windows partition is actually mounted.  Usually it'll mount in something like 

/media/os/

Or something like that.  Maybe someone that knows samba better than I will know better how to search.  But I'd know it just by looking at your df, probably.

---

### Post by llamabr on 2009-07-20
/smb://blitz/blitz_a%20(e)/My%20Pictures

Also, if you can get to that folder in terminal, then just look at the output of:

```
pwd
```

---

### Post by zzyzx1 on 2009-07-20
This is a dedicated machine, no windows partition here... I think its puking around this: blitz_a%20(e), the %20 and the () gets negative vibe outputs when I enter... maybe need to rename windows shared drives to something more friendly...??

---

### Post by llamabr on 2009-07-20
That may be.  cli doesn't use the %20, but rather like this

/home/brock/file\ name\ with\ spaces.pdf

Maybe fixing the file name will help.  And it may be that screensaver just can't access them over samba (though I sort of doubt this).  Would it kill you just to keep the pics on the linux box?

---

### Post by zzyzx1 on 2009-07-20
TOOOO many pics to move over to Ubuntu machine... i will change drive names and add symlink and try. Kid to bed first.... thx

---

### Post by zzyzx1 on 2009-07-20
When i do the Symlink i get this: syntax error near unexpected token `('

I cant change the share name on Windows drive blitz_a (e) where e is the windows assigned drive letter.... any CLI way around this...??

---

### Post by llamabr on 2009-07-20
I'm no expert about anything windows.  But if you're making the symlink in cli, try tab completion.  It should just give you whatever it wants.

---

### Post by SoftwareExplorer on 2009-07-20
If you want to get to samba shares with the CLI the real place it is mounted in is /home/yourusername/.gvfs/nameofshare.

---

### Post by zzyzx1 on 2009-07-20
Yeah, but that doesnt help the disconnect between term cli syntax, screensaver config file syntax and samba file/path/syntax.... they dont appear to be singing from the same book..!

---

### Post by zzyzx1 on 2009-07-21
can anyone elaborate on this for me? I dont fully understand the structure... edit/save

By default, screensaver "slideshow" shows pictures from "$HOME/Pictures".

You can specify another directory by defining "XDG_PICTURES_DIR" in
${XDG_CONFIG_HOME:-$HOME/.config}/user-dirs.dirs

ex:
echo XDG_PICTURES_DIR="/path/to/another/dir" >>
${XDG_CONFIG_HOME:-$HOME/.config}/user-dirs.dirs

---

### Post by llamabr on 2009-07-21
so do this.  Using terminal, navigate to the place that the pictures are:

/home/whatever/.gvfs/file/file/whatever/pictures

use tab completion to get there if you have to.  When you get there, do:

```
ls
```

to make sure all the files you want are there.  Then do:

```
pwd
```

and that will tell you the path the the dir that you're in.  It will use the syntax that it wants, and you can just copy that.

---

### Post by zzyzx1 on 2009-07-21
I changed the windows share name from- Blitz_A%20(E) to now just E without the other junk.

This seems to play nice and it comes up nice in the network browser. I can get to the dir from browser.

Anytime i try from cli i get "Nosuch file or directory".

So I must have a mapping/mount problem i think??

---

### Post by llamabr on 2009-07-21
So it's working now?  If not, copy out exactly what you're doing, and what error you're getting.  with tab completion, you should never get 'no such file or directory'.

---

### Post by CatKiller on 2009-07-21
> **zzyzx1 said:**
> I dont fully understand the structure...

That's because it's abstracted to be flexible. ${XDG_CONFIG_HOME:$HOME/.config}/user-dirs.dirs boils down to ~/.config/user-dirs.dirs. If you look in that file you'll see that a bunch of special directories are specified, such as XDG_DESKTOP_DIR="$HOME/Desktop" specifying that the Desktop directory is ~/Desktop, and so on.

Just find the location that you're interested in in a file browser window, open your ~/Pictures directory in another window and middle-click and drag the one onto the other. In the menu that comes up select Link Here. This will make a symbolic link from ~/Pictures to where you're keeping your pictures and, as long as your other location is mounted, pictures from that location will show up in the Slideshow screensaver.

You seem to be making this much more difficult than you need to.

+1 on the Tab-completion.

---

### Post by misswham on 2009-07-21
didnt know about the screensavers.  thanks.

---

### Post by zzyzx1 on 2009-07-21
"You seem to be making this much more difficult than you need to."


No kidding! but its not by choice... you only have to go through about 100 posts before you realize that the instructions/options that your given only apply if YOUR system completely mirrors that of the the person making the post!

Back to the thread - I have added my smb:// path of my newly named shared drive hanging off the Windows machine in all of the screensaver tweaks and it doesnt work. I try to access the shared drive via cli and get the "not a valid directory" error.

I can browse to the windows net/folders without a problem. I still have the question/issue of the Ubumtu cli syntax, ie, drive-> "biltz/E/My%20Pictures" (machine/drive/folder) The %20 I think is still part of the problem. I should probably change it on the Window side to My_Pictures... thoughts?

I have tried it every wich way in the cli and it still gets an error when simply trying to access the share via.

What commands should i used "in cli" to verify if shared drive is mounted properly and what about spaces/%20 in the cli?? Yes, I am a NUB but what better way to learn than spending a week jerking around with making a screensaver do what you want it to do!

Thx

---

### Post by CatKiller on 2009-07-21
> **zzyzx1 said:**
>  Back to the thread - I have added my smb:// path of my newly named shared drive hanging off the Windows machine in all of the screensaver tweaks and it doesnt work.

This is the bit that you're making unnecessarily hard. Rather than messing about with config files, make the symlink. This is one of the main reasons for symlinks existing.

> 
 I try to access the shared drive via cli and get the "not a valid directory" error.

Use Tab-completion. You start typing the name of a program or file/path and then press Tab. If there's a unique way to complete the string, the shell will do so for you. If there's more than one way to complete the string the shell will complete as much as it can and then beep at you. Pressing Tab twice as this point will show you the ways that the string can be completed. Type in as many letters as it takes to get a unique result and then press Tab again to complete the rest.

So, for example, you might use ```
cd .gvfs/<TAB><TAB>
```to see what directories the shell thinks is in ~/.gvfs. You'll probably find that all "unusual" characters, such as space, or &, or whatever are "escaped" by preceding them with a \ character, so that the shell knows that they are part of the filename and not something that needs to be interpreted and acted upon.

---

### Post by zzyzx1 on 2009-07-22
"Just find the location that you're interested in in a file browser window, open your ~/Pictures directory in another window and middle-click and drag the one onto the other. In the menu that comes up select Link Here. This will make a symbolic link from ~/Pictures to where you're keeping your pictures and, as long as your other location is mounted, pictures from that location will show up in the Slideshow screensaver."

I get 2 windows that open when i created the link> 

1) "The Link "My Pictures" is Broken. Move it to trash?"
2) Opening "My Pictures" and this just stalls...

---

### Post by CatKiller on 2009-07-22
> **zzyzx1 said:**
> I get 2 windows that open when i created the link> 

1) "The Link "My Pictures" is Broken. Move it to trash?"
2) Opening "My Pictures" and this just stalls...

Where did you make the link to? And, assuming that you created the link in ~/Pictures and called it "My Pictures," what does ```
ls -l Pictures/My\ Pictures
``` return?

---

### Post by zzyzx1 on 2009-07-22
ls: cannot access Pictures/My Pictures: No such file or directory

I did get it working, though! I had to download and use older xscreensaver (which has better configurables) and i put the ls path of -> /home/john/.gvfs/e on blitz/My_Pictures (notice i had to add the _ on the windows side) and it works great, that is...

When i reboot xscreensaver and gnome screen saver are figting it out.

Also, i created an executable sharemount.sh in /home/john/sharemount.sh and added it to the start up but it doesnt re mount after boot. in fact a couple of files i put in start up arent working.

The symlink is just not working, which i would use for the gnome screensaver. xscreensaver is kind of old-skool...

---

### Post by CatKiller on 2009-07-22
> **zzyzx1 said:**
> ls: cannot access Pictures/My Pictures: No such file or directory

So what *did* you call your link, then?

> 
When i reboot xscreensaver and gnome screen saver are figting it out.

 
As you've noticed, xscreensaver is **much** easier to customise than gnome-screensaver. When gnome-screensaver was introduced as the default instead of xscreensaver, quite a large number of people pointed out that the extreme lack of configuration options - in particular, the inability to easily set the pool of screensavers that would be used for the Random setting - was, in fact, a flaw. The single dev marked every single bug report as WONTFIX.

As a result there are quite a number of threads detailing exactly how to consistently replace gnome-screensaver with xscreensaver.

---

### Post by llamabr on 2009-07-23
I have been fighting the urge to tell you to install xscreensaver since this thread started.  It's much more configurable, but as the gnome was is made for gnome, and your problem **is** solvable, I was trying to help you solve it.

As you said, this is a good chore to help you understand a bit more about how your system works.  One thing you learned is to think laterally, and use something else, which is a valuable tool.  But another would be to actually solve this.  A better understanding of how your file structure works would do, and will keep this sort of thing from occuring again.

---

### Post by zzyzx1 on 2009-07-23
> **llamabr said:**
> I have been fighting the urge to tell you to install xscreensaver since this thread started.  It's much more configurable, but as the gnome was is made for gnome, and your problem **is** solvable, I was trying to help you solve it.

As you said, this is a good chore to help you understand a bit more about how your system works.  One thing you learned is to think laterally, and use something else, which is a valuable tool.  But another would be to actually solve this.  A better understanding of how your file structure works would do, and will keep this sort of thing from occuring again.

Yep... agreed. I found some other fixes but will stick with "if it aint broke..." for now. Its working great!

Now, if I could get stuff to load/mount at strat up i will be out of the woods for a while. I just posted in Beginners.

Thanks.

---

### Post by 999terry on 2009-08-10
My problem is I have just installed Xubuntu 8.04 which works amazingly quickly on my HP 500a Pentium machine even with only 256mb ram - but when the screen goes into save mode there is 'no image'. I have set the 'Cosmos' images to appear but they do not come up - any suggestions?

---

### Post by resander on 2009-08-11
If photos from [www.webshots](www.webshots) qualify as screensavers you can go to [www.webilder.org](www.webilder.org) and download a program that will let you use webshots images on Ubuntu.

---

### Post by colau on 2009-08-16
Webilder is also here
[http://www.getdeb.net/app/Webilder](http://www.getdeb.net/app/Webilder)

---

### Post by Windows Nerd on 2009-08-16
For the person who wanted to have his background to change through a slideshow of pictures, there is a program called Background Buddynthat makes your background change every 5,10, 15 or however many seconds you specify. If you have seen on a Mac how you can get your background to change, it works somewhat like this.

Hope this is useful

Scott

---

