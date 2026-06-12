---
title: "How to remove Djl"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by thorbs on 2010-10-17
Hi I have tried out Djl, with out success. Now I want to uninstall it. I read in another thread that one could just erase the folder that djl was upacked in, but that clearly does not do the job. Any suggestions?

t.

---

### Post by Bölvaður on 2010-10-17
How did you install it mate?

If it just runs from one folder then it is enough to just remove that folder.
If you compiled it or made some script move the files into different places when you installed it, then we'll need to hunt them down, I didn't see an uninstaller.

as a test pasted this into the terminal:
```
locate Fopen.py
```
and also
```
locate maj.png
```
hope it will tell us something.

---

### Post by thorbs on 2010-10-19
Dear sir, good point, I guess I need to become more aware of my use of the command line. 


I used the commands formula:

tar zxvf <archive-name>
cd <extracted-archive-dir>
chmod +x djl.sh
./djl.sh 


archive was my archive named "spil" the one I tried to erase without succes


I found the command formula on a webpage that presented the djl program. 

when I use the command locate Fopen.py I get back:

/home/thorbs/.local/share/Trash/files/spil/djl/djl/libs/Fopen.py
/home/thorbs/djl/djl/djl/libs/Fopen.py


When I use the command locate maj.png I get back:

/home/thorbs/.local/share/Trash/files/spil/djl/djl/res/maj.png
/home/thorbs/djl/djl/djl/res/maj.png


Just an extra question is there a right way to install interesting programs one find, and how do I make sure I stay on top of it?



thanks for your time

---

### Post by thorbs on 2010-10-23
I have had trouble removing DJL, a program I installed not using the softwarecenter. I wanted to reinstall it, but when I did the old settings where still there, even though I un-installed it. Then I tried to completely uninstall it. But it still says djl in my games section in the program section, now though with a symbol with a question mark.

To uninstall I removed the folder it installed in, to the trash. I had read that was suppose to do the job.

I have tried to ask here, maybe not specifick enough. 

I am reading the book a practical guide to Ubuntu linux, and there it says that I should be able to get a add/remove application window up by typing 
gnome-app-install in my terminal. But I have no luck with it.

any help?

---

### Post by uRock on 2010-10-23
Related threads merged.

---

### Post by s3n1d on 2011-02-11
don't remove just go on repositori /on menu in djl/ -->libaries manager found libery and instal it




question

how can i run game in diferent resolution i downloaded cube but when i run it i got mesage out of range 1024x768

how i can run game in 800x600 resolution


[COLOR=Red]my english are very bad i apologize for errors in post[/COLOR]

---

### Post by Kir_B on 2011-09-06
> **thorbs said:**
> Hi I have tried out Djl, with out success. Now I want to uninstall it. I read in another thread that one could just erase the folder that djl was upacked in, but that clearly does not do the job. Any suggestions?

t.
[FONT=System]Well, I can't help with the removal problem, but perhaps I can help, by giving you a reason not to even want to uninstall it. I was having a similar problem with my djl  installations. I installed mine via the [getdeb games repository]("http://www.playdeb.net/updates/Ubuntu/11.04#how_to_install") on two  different machines running lucid (one upgraded from Jaunty and Karmic  and the other, a fresh install of 10.04.2).
  
On the fresh install:
After installing djl, there was no entry to be found for it in the games  section of my main menu, so I had to create a launcher: -> Preferences  -> "Main menu". In the left column, I highlited "games", and then  selected "+New Item". In the new item box, I put djl (a small D, J, and L) in  the name and command entries, plus a brief description (djl games manager),  and then OK.
  
On the upgraded O.S.:
Once installed, there was an entry for djl, minus an icon, located in  the games section of the main menu. Using the same method as above would've worked fine, but instead, I dragged the invisible icon up to my panel, right  clicked the strange icon that djl acquired once it established itself on  the panel and selected properties. In the properties dialog, just like above, I changed  the command to just "djl" (minus the quotes), closed the properties box  and clicked the icon to confirm that it worked. Done!
  
[/FONT][FONT=System]I know this is a little late for  thorbs, et al, (and definitely doesn't help with the uninstalling issue, which isn't a problem for me. Other than the menu entry remaining after removal, I can uninstall the rest of it {I think}), but  perhaps this will help some of you folks, at least get djl up and running. 

Let us know if this was helpful for you.
  
Peace all. ):P  Kirby[/FONT]

---

