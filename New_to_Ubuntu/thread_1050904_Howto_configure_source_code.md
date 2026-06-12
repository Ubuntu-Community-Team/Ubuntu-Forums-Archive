---
title: "Howto configure source code?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by harrkou on 2009-01-26
One last q for today:) What do they mean when they say "configuring source code" and how can this be done?

---

### Post by abhilashm86 on 2009-01-26
modifying is better word to configure.............
You can open the written O.S or application program in your favorite editor like emacs,nano,vim,gedit n others........

then u can alter source code in order to better use,simple example u can create shortcut keys,alter servers n others........

take an example

go to terminal,to view your init boot up program,type

gedit /boot/grub/menu.lst

view it,try adding bootsplash images,reduce boot start time n others,enjoy open source,got it friend:)

---

### Post by abhilashm86 on 2009-01-26
hey check man for more details,because it explains each part of the application.The path for saved files can be found in man,
like 
man vim
it gives usage of editor and also files...........

---

### Post by nothingspecial on 2009-01-26
If I`m right you`re asking about the first step in compiling.

This is usually ./configure  (but not always)

Included in the source code is a configuration tool. When you type ./configure you run it.

(As far as my understanding goes and as basically as possible) It kind of checks your computer out to see if you have the necessary stuff to run the application, such as the correct dependencies and all the right files in the places the app expects them to be.

[[COLOR="Magenta"]This[/COLOR]]("http://www.webmonkey.com/tutorial/Compile_Software_From_Source_Code#Building") explains it better than me.

---

