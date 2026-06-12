---
title: "Store and retrieve pieces of text in terminal"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by jjei on 2010-10-18
I find myself often in a situation where I am writing a terminal command and then I want to use a piece of text I have previously used.

I now I can use arrows to scroll previous commands. I know I can use ctrl+r to search history. But this is not what I want.

I want to be able to somehow paste some predefined pieces of text in the middle of a command.

An example (I am using drupal and drush):

I write drush dl something and then I want to add "--uri=http://somedomain.com" by hitting a keystroke.

Is there anyway to achieve this? A "place" where I can store multiple pieces of text and then use some keyboard shortcut to paste them?

Thanks in advance!!

---

### Post by da burger on 2010-10-18
The only thing I could think of would to be an alias. Just add an alias for the command you want to use over and over again to your .bashrc file. The format is: ```
alias thingYouWantToType='thing you want to run'
```
Hope that helps
Angus

---

### Post by Hippytaff on 2010-10-18
you can store them in a text file (echo command/url >> mytextfile.txt) and paste them by *cating the text file, highlighting the text CTRL+SHIFT+C to copy CTRL+SHIFT+V to paste
 
*```

cat mytextfile.txt

```

---

### Post by Hippytaff on 2010-10-18
> **da burger said:**
> The only thing I could think of would to be an alias. Just add an alias for the command you want to use over and over again to your .bashrc file. The format is: ```
alias thingYouWantToType='thing you want to run'
```
Hope that helps
Angus
 
This is probably a much better solution ;-)

---

### Post by JKyleOKC on 2010-10-18
In Xubuntu (which is the variant that I use) there's a panel applet called "clipman" that's a clipboard manager. When clipman is running, it stores everything that you've cut or copied to the clipboard in its own buffers, and you can click on its panel icon to see an index of the stored data. You can highlight any entry in that list, and it becomes the current clipboard content so that you can paste it into whatever text you are editing at the time.

I'm sure that similar packages exist for straight Ubuntu and for the Kubuntu variant, but I don't know their names. You might try doing a Google search for "ubuntu clipboard manager" to see what turns up; such managers appear to be exactly what you are looking for.

---

### Post by fancypiper on 2010-10-18
Parcellite seems to be highly recommended for a clipboard manager

---

### Post by jjei on 2010-10-19
Thanks. However, alias doesn't work. If I use
drush myalias
I get errors because alias is a part of the command. Similarly if I have some alias defining a directory and I use
cd somealias
the command is not executed.

I haven't tried parcellite yet.

---

### Post by HermanAB on 2010-10-19
Highlight and middle click?

---

### Post by da burger on 2010-10-19
> **HermanAB said:**
> Highlight and middle click?

Seconded.

Yes, aliases only work if the alias is the first thing in the command. So instead of ```
cd myalias
``` you need to build "cd" into the alias, something like: ```
alias cddir='cd /path/to/dir
``` should work.

Alternatively if you prefer, put the options and file name in a variable in your bashrc file. ```
var="file --options"
``` and call it using ```
drush $var.
```
Regards
Angus

---

### Post by jjei on 2010-10-25
Awesome!! The variable approach is perfect since the thingies are parameters and so I can't use alias. Thank u!

---

