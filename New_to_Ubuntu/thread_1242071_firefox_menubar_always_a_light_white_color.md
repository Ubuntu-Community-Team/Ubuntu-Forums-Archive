---
title: "firefox menubar always a light white color"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by libihero on 2009-08-16
i dunno what i did, but now no matter what theme i choose, in firefox the menu bar (file, edit, etc) is always a white-greyish color font

---

### Post by rednano12 on 2009-08-16
Could you please post a screenshot? (Alt-Printscreen will take a screenshot of the current window and put it on your clipboard.)

---

### Post by libihero on 2009-08-16
here's a screenshot
this happens ONLY in firefox, everything else is normal

---

### Post by libihero on 2009-08-17
bump

---

### Post by fooman on 2009-08-17
have you tried changing the firefox theme?

look here:

[https://addons.mozilla.org/en-US/firefox/search?q=&cat=2%2C0](https://addons.mozilla.org/en-US/firefox/search?q=&cat=2%2C0)

find a theme you like,  click "add to firefox" and restart firefox when prompted to switch to the new one.

in firefox's toolbar,  go to tools > addons > themes tab to change back or choose another theme you have downloaded.

i am currently using this one with my firefox 3.5:

[https://addons.mozilla.org/en-US/firefox/addon/8076](https://addons.mozilla.org/en-US/firefox/addon/8076)

looks great with the dark gnome theme i am using.  :)

---

### Post by libihero on 2009-08-17
the problem is something happened, i dunno what, and now the menu options are always light
like is there any way to find out what or change it back to its default??

---

### Post by libihero on 2009-08-19
bump...

---

### Post by tarps87 on 2009-08-19
Try Edit -> Preferences -> Content -> Colours and tick the box use system colours

---

### Post by libihero on 2009-08-19
nope didnt work :(
here's another example of what im talkin about, using the "simple" theme...
its only firefox which is like that...
is there any way i can completely remove firefox and reinstall it so it has the standard options?

---

### Post by libihero on 2009-08-19
btw i tried downloading a new type of theme but it still had the same problem

---

### Post by libihero on 2009-08-20
bump...

---

### Post by fooman on 2009-08-20
have a look in system > appearance > customize button

look under the "colors" and "window borders" tabs....see if changing those has any effect.

hope that helps.

---

### Post by Strange_Movement on 2009-08-20
Try typing ***about:config*** in the address bar,
then add ***ui.menutext*** as a string key,
and finally make ***ui.menutext*** = ***black***

Hope that helps

---

### Post by libihero on 2009-08-20
i did this, even with spaces like "ui.menutext = black", but it still didnt work :(

---

### Post by Strange_Movement on 2009-08-20
Sorry I'll try and be a bit more concise with my instructions

1) Enter ***about:config*** in the address bar
2) Click the ***I'll be careful, I promise!*** button
3) Right hand click anywhere in the list of stuff that appears and then select ***New***, then ***String***
4) In the ***Enter the preference name*** field in the ***New string value*** window enter ***ui.menutext***
5) In the ***ui.menutext*** field in the ***Enter string value*** window enter ***black***
6) Close Firefox
7) Open Firefox

...and voila, black text in Firefox menus !

This solved the problem for me when I installed a Gnome theme that messed up the Firefox theme I had installed. It appears that Firefox may not correctly handle Gnome themes.

I hope that's a little more useful to you.

---

### Post by annuityjobs on 2009-08-20
Fooman thanks for the add-ons.:guitar:

---

### Post by Strange_Movement on 2009-08-20
...sorry I should have attached a picture as well, so here it is

---

### Post by Sir Jasper on 2009-08-20
Hi Strange_Movement,

Thank you for your explicit and helpful instructions - I was able to change my text colour from black to blue (where I typed ¨blue¨ as the last step).

My regards

---

### Post by libihero on 2009-08-20
gahh still didnt work :(
it changed all the other texts to black, such as search history, but the menu stays white! :(

---

### Post by fooman on 2009-08-20
have you tried making a new firefox profile and see if that behaves the same?

open a terminal and run this:

       ```
firefox -ProfileManager -no-remote
```


create a new profile, highlight it in the list and click "start firefox"

---

### Post by running_rabbit07 on 2009-08-20
Maybe you need my theme?

---

### Post by Sir Jasper on 2009-08-21
Hi libihero and helpers,

Especially if you have a clone/backup perhaps you could try:

* Exporting your existing bookmarks to an HTML file.

* Making a note of your addons

* Uninstalling Firefox

* Re-installing Firefox

* Importing bookmarks from the HTML file

* Reintoducing your addons from your manual checklist

Perhaps an experienced helper would comment on this thought.

My regards

---

### Post by Strange_Movement on 2009-08-21
OK, I've got to suspect that it's going to involve one of the user interface preferences that are held in ***about:config***. Maybe what **libihero** should do is post all of his ***about:config*** preferences filtered by ***ui.***
Then we could compare them to those shown at [COLOR="Blue"][http://www.mozilla.org/unix/customizing.html#ui]("http://www.mozilla.org/unix/customizing.html#ui")[/COLOR] and maybe work out what to change.

---

### Post by libihero on 2009-08-21
ok how do i show all the about:configs?  i really dont mind reinstalling firefox.  i tried before tho but it didnt change anything.

---

### Post by fooman on 2009-08-22
i don't think reinstalling will help.

did you try making another profile?  

open a terminal and run this:

           
```
firefox -ProfileManager -no-remote 
```create a new profile, highlight it in the list and click "start firefox"

see if the new profile has the same problem.

---

### Post by Strange_Movement on 2009-08-22
Sorry for the delay replying libihero, I've just been told I've got a job after 6 months unemployment !

Anyways to filter all the ***ui.*** preferences do the following:

1) Enter ***about:config*** in the address bar
2) Click the ***I'll be careful, I promise!*** button
3) Now in the field named ***Filter:*** at the top of the page enter ***ui.***
4) You should now have a list of only those preferences starting with the characters ***ui.*** (that's the letters "**u**" and "**i**" and a full-stop or period if you're American "**.**")
5) Take a screenshot like the one I have attached and post it back here

Now hopefully we can have a look at those user interface preferences and maybe work out which one is causing a problem.

---

### Post by texpat on 2009-08-22
I'm not at my ubuntu box so I can't test this, but could it be that you accidentally changed accessibility settings? I don't even know if its possible to have application specific ones, but its a thought ;-)

Tx

---

