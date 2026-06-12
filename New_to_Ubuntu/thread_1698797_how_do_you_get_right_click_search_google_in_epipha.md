---
title: "how do you get right click search google in epiphany?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by el_koraco on 2011-03-02
i'm using maverick with a 2.6.35.27 kernel, epiphany version 2.30.2, just installed the browser yesterday. i've never thought i'd want to replace chrome, but i've made the switch in just a day. 

i do have a strange question. is it possible to add a "search google" option in the right click menu? i've been looking in gconf files, and can't seem to find it, and googling also doesn't help. 

thanks.

---

### Post by kerry_s on 2011-03-02
there use to be a extension(smart bookmarks) for that, but i think they moved it to the url bar. when you type/paste in there you should see a "search the web", i know it sucks.

---

### Post by el_koraco on 2011-03-03
smart bookmarks still exists, i.e., you can set the search the web option to include search yahoo, bug reports, pornhub... :D
i was just wondering if i'm going crazy, not being able to find this right click option. what a strange move to make.

---

### Post by kerry_s on 2011-03-03
> **el_koraco said:**
> smart bookmarks still exists, i.e., you can set the search the web option to include search yahoo, bug reports, pornhub... :D
i was just wondering if i'm going crazy, not being able to find this right click option. what a strange move to make.

yeah, the old way was better. they even still have it in the help, see pic, epiphany is my backup browser.

---

### Post by el_koraco on 2011-03-03
ok, so i found the actions extension, and it lists as: 

> To create an action, perform the following steps:
					

   1.


      							Choose Edit &#9656; Actions
      							to open the Actions manager
      						
   2.

      							Press Add to add a
      							new action
      							
      						
   3.

      							In the "Add Action" window, 
      								
          *

            										Enter the Name of the action. The name
            										will be displayed in the context menu
            									
          *

            										Enter the Description of the action.
            										The Description will be displayed in the
            										statusbar of Epiphany and in the Action
            										Manager
            									
          *

            										Enter the Command to execute. this
            										command will be executed and will receive as
            										argument the element on which you'll launch
            										the action. This action can be any
            										program or script available in your path
            									
          *

            										Select Pages or
            										Images to choose on
            										which elements the action will appear
            									
          *

            										Press Add
            									

      							
      						
   4.

      							Press Close to close the Actions Manager

now, does anybody know which command you gotta run to get epiphany to search google?

---

### Post by el_koraco on 2011-03-03
you just select the text and press the middle mouse button:lolflag:
it's always the easiest thing

---

### Post by kerry_s on 2011-03-03
> **el_koraco said:**
> you just select the text and press the middle mouse button:lolflag:
it's always the easiest thing

don't work for me. :confused:

got it! you have to turn on middle click open url in gconf-editor.

---

