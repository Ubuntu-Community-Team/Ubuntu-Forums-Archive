---
title: "GTK+ programmng for dynamic text display"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by teohoeeng on 2009-06-01
Hi, all.
I am very new to GTK+ 2.0. I just started to use it to build a very simple GUI for my robot under Ubuntu 7.10. I am trying to get the GTK+ to display my robot's sensors data at certain time intervals. Right now, I am using gtk_entry_get_text() and it can only displays once after the GUI is launched and the program waits at gtk_main().
 
I tried to create a timer handler to update the sensor data at 5Hz rate or even use another thread to do it, but the text won't change. It is always showing the very first text displayed when GUI is launched.
 
As I am very new to this GUI and do not wish to spend too much time in complicated GUI design as it is not my focus, is there a simple solution to dynamic numeric data display? 
 
Appreciate any help and advice. Thanks.
 
Regards
Ken
[IMG]http://www.linuxforums.org/forum/linux2/statusicon/user_offline.gif[/IMG]

---

### Post by niteshifter on 2009-06-01
Hi,

Couple 'o things:

You'll catch more fish when you fish where they're biting. Meaning: Try the programming area of the forums.

Now a quick answer for your problem. How you implemented the timer is key: it's event must be available to gtk_main(). 

You may find this [link]("http://zetcode.com/tutorials/gtktutorial/gtkevents/") useful. Near the bottom is a timer example.

---

### Post by teohoeeng on 2009-06-01
Thanks. I have posted the question to the programming talk forum.
 
I have seen that website you attached, but those deosn't really relate to my issues. My timer is triggered every 0.2s and it will update the numeric text. The problem I realize is how I can use the gtk_g_connect() to connect this update mechanism to the callback function which will use gtk_set_text() to update the new text display. I tried to use any button I have to test out. It works, but I have to keep pressing the buttons to update the display. I want to make it automated at regular intervals based on my timer rate. I suppose it is an easy problem.
 
Not sure how to do it though. Hopefully i get some good reply from the programmer talk forum too. Thanks.

---

