---
title: "How to use a premade Conky config"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by pckrfan75 on 2011-08-13
I downloaded a cool looking conky configuration but am struggling figuring out how to use it. The file I downloaded contains a text file, a wallpaper, and a .lua file. Both the text file and the .lua file seem to be the configuration, and unlike the last time I configured conky, copying and pasting the text file into my .conkyrc is not seeming to apply the settings. any thoughts?

---

### Post by Frogs Hair on 2011-08-13
Here is a good place to start with Conky .[http://ubuntuforums.org/showthread.php?p=5436679#post5437628](http://ubuntuforums.org/showthread.php?p=5436679#post5437628)


There are some things to do before installing a theme or using / making a Conky configuration .
Code:

sudo apt-get install conky-all

Code:

sudo apt-get-get install lm-sensors

Code:

sudo sensors-detect

Answer yes to all questions. At this point you can close the terminal and start Conky by using Alt+F2 and enter
Code:

conky

To stop Conky use Alt+F2
Code:

killall conky

---

### Post by Frogs Hair on 2011-08-13
You could post a link to the theme as well  , because each theme /configuration may require different steps .

---

### Post by pckrfan75 on 2011-08-13
[http://bigrza.deviantart.com/art/Suuuuny-conky-153331007](http://bigrza.deviantart.com/art/Suuuuny-conky-153331007)

That is the config. I have moved the main text file to my /.conkyrc as usual, and then i put the .lua file into my home folder and changed the coding of the .conkyrc file to direct it towards that. I can't forsee any issues with why this is not working...

---

### Post by Frogs Hair on 2011-08-13
> **pckrfan75 said:**
> [http://bigrza.deviantart.com/art/Suuuuny-conky-153331007](http://bigrza.deviantart.com/art/Suuuuny-conky-153331007)

That is the config. I have moved the main text file to my /.conkyrc as usual, and then i put the .lua file into my home folder and changed the coding of the .conkyrc file to direct it towards that. I can't forsee any issues with why this is not working...

I'm using a different widow manager at the moment , will login to Unity and test it out .

---

### Post by pckrfan75 on 2011-08-13
> **Frogs Hair said:**
> I'm using a different widow manager at the moment , will login to Unity and test it out .

Thanks much!

---

### Post by Frogs Hair on 2011-08-13
I'm trying to get it to work and my screen turns black . Another user had this problem , but the creator of the configuration never responded . I will have to figure out how to change the resolution because it was made for 1440 x 900 and I run 1280 x 1024 . I will get back to you .

---

### Post by pckrfan75 on 2011-08-13
> **Frogs Hair said:**
> I'm trying to get it to work and my screen turns black . Another user had this problem , but the creator of the configuration never responded . I will have to figure out how to change the resolution because it was made for 1440 x 900 and I run 1280 x 1024 . I will get back to you .

As far as the screen being black, in your conkyrc file, change it the window type to desktop instead of override. I was able to fix that, and now I got the text to show up, just need to like you change from 1440x900 into my resolution of 1600x900.

---

### Post by Frogs Hair on 2011-08-13
I think my problem is that I don't have Cairo Dock installed . It says cairo required in the script ?? . I saved the files to location specified by the  .lua text script and all I get is a black screen . When I change the .rc to override nothing appears .

---

### Post by pckrfan75 on 2011-08-13
I'm not sure why you would need cairo-dock for this but even before you deal with the .lua, i had a black screen. Just change override to desktop under the conkyrc file and that will go away. Any tips on how to change the resolution of that .lua file though? I figured out how to do it for the conkyrc, just not the .lua

---

### Post by Frogs Hair on 2011-08-13
> **pckrfan75 said:**
> I'm not sure why you would need cairo-dock for this but even before you deal with the .lua, i had a black screen. Just change override to desktop under the conkyrc file and that will go away. Any tips on how to change the resolution of that .lua file though? I figured out how to do it for the conkyrc, just not the .lua

I doesn't work at all when modify the .rc . Try entering width and hight on this line of .lua text . Replace the letters with your resolution .

conky_window.drawable, conky_window.visual, w, h)
	cr=cairo_create(cs)

---

### Post by pckrfan75 on 2011-08-13
> **Frogs Hair said:**
> I doesn't work at all when modify the .rc .

That surprises me. But oh well. That is my only guess...

---

### Post by Frogs Hair on 2011-08-13
I just noticed that the .lua text is read and write only when I looked in properties . You may need check the execute box in properties > permission .

---

### Post by pckrfan75 on 2011-08-13
> **Frogs Hair said:**
> I just noticed that the .lua text is read and write only when I looked in properties . You may need check the execute box in properties > permission .

My ability to resize isnt from lack of permissions, I am being able to edit it, just not sure what to edit to make it fit.

---

### Post by Frogs Hair on 2011-08-13
> **pckrfan75 said:**
> My ability to resize isnt from lack of permissions, I am being able to edit it, just not sure what to edit to make it fit.

I can only see a black box so I can't be of any help . I have tried changing hight and width in all of the locations that might work .

---

### Post by pckrfan75 on 2011-08-13
> **Frogs Hair said:**
> I can only see a black box so I can't be of any help . I have tried changing hight and width in all of the locations that might work .

Figured it out, I actually changed each component of the positioning of each text feature... Pain in the *** but it worked.

---

### Post by Frogs Hair on 2011-08-13
> **pckrfan75 said:**
> Figured it out, I actually changed each component of the positioning of each text feature... Pain in the *** but it worked.

According to the comments posted with the theme it was supposed to be easy .I'm glad it's working , I have never had a black box appear with any other theme and it is hard to move things around when you can't see them .

---

### Post by pckrfan75 on 2011-08-13
[IMG]http://imageshack.us/photo/my-images/190/mynewdesktop.png/[/IMG]

That is what mine looks like. And theoretically, it was easy, it was easy to figure out. It was just a pain to get the coordinates correct.

---

