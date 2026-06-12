---
title: "Help with a few of problems"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by robro on 2011-02-14
Hello, I have been using ubuntu for a few weeks and i have been impressed by it more and more every day :D but there are few things i don't quite understand how to do (or is even possible):
1. unable to set arguments(?) for shortcuts (eg: gnome-terminal cd ~/Downloads)
2. when i make a program executable (eg a bash/shell script) it prompts if i want to display/run/run in terminal, is there a way to set a default for ONLY one file and all others would prompt for it?

Thanks for your answers :)

---

### Post by shunan on 2011-02-14
Trying to do things the windows way in linux? well, i think it is a bad idea...

1. 
gnome-terminal --working-directory=/home/shunan/Downloads

try: man gnome-terminal for more

linux way: first if you want to open terminal you can use the keyboard shortcut Ctrl+Alt+T, alternatively you can open a terminal inside nautilus!
a: sudo aptitude install nautilus-open-terminal
b: nautilus embedded terminal (i hate this):
[http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html](http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html)

If you still want a shortcut it is a good idea to write a script! I guess that is what led you to the second question...

2.
as far as I know this is the default behavior, frankly speaking don't know and never had the need! If you want to create a shortcut to gnome-terminal with a specific working directory on the desktop, I would suggest you to right click on the desktop and create a launcher with command as 

gnome-terminal --working-directory=/home/shunan/Downloads

make changes as needed

advice: when you are using Linux think like Linux (not like windows)

---

