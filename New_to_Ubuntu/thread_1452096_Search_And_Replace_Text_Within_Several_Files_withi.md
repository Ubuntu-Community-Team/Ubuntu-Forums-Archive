---
title: "Search And Replace Text Within Several Files within a directory"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by faraz_k86 on 2010-04-11
so basically here is the thing.. i have a whole lot of files.. around 2000 of them and I have to find a certain code in all of them and replace them with something else.. how do I do this?

I want something that can search within all the files.. bring up the files that has the code and then replace it..

notepad++ in windows is capable of doing this.. any one know how to do this in linux?

I found this via Google but the terminal commands dont seem to be in ubuntu. : [http://www.linuxforums.org/forum/linux-programming-scripting/39664-search-replace-text-within-several-files.html](http://www.linuxforums.org/forum/linux-programming-scripting/39664-search-replace-text-within-several-files.html) and [http://www.webune.com/forums/linux-shell-command-find-and-replace-text-within-files-t157.html](http://www.webune.com/forums/linux-shell-command-find-and-replace-text-within-files-t157.html)

---

### Post by nothingspecial on 2010-04-11
A combination of find, awk, sed and xargs mixed with a dash of regular expression, I would imagine.

If you can be more specific, maybe someone can write it for you.

---

### Post by faraz_k86 on 2010-04-12
thx but thats too complicated.. there should be an application that can do this. for example like i said in my first post notepad++ can do this.. isnt there any application that can do this by default..

Now to be more specific. I have a joomla website that got hacked. what the hacker did was put a virus script in all of the index.php and index.html files.. the virus code is in the form of <script> lsjdu&^%$........</script>

The problem is that joomla has hundreds of index.html files.. 

I have downloaded all of the files from my server onto my local hard drive and now want to search and replace this script text in all files..

---

### Post by faraz_k86 on 2010-04-12
anyone?

---

### Post by gmargo on 2010-04-12
> thats too complicated.. there should be an application that can do this.Quite frankly, you seem unwilling to learn or to make an effort.

Your first post was 20 hours ago.  If you had buckled down with find, sed, awk etc, you would have been finished 19 hours ago.

And your main assertion seems to be that "notepad++ can do it!".  Well, then, move the files over to your windows machine and fix them there.  Or export the filesystem with samba and you won't even have to move them.  Too complicated?

---

### Post by nothingspecial on 2010-04-12
```
regexxer - A visual search and replace tool
replaceit - quick, light and effective text replacement tool
rpl - intelligent recursive search/replace utility
searchmonkey - search files using regular expressions aiming to replace find/grep tools
```

results of apt-cache search

Never used any of them, but give one of them a go

---

### Post by Martje_001 on 2010-04-12
Try 'sed' on the commandline:
```
sed -i 's/text in file/replaced text/g'  *
```
**sed:** command used
**-i:** edit files in place
**'s:** replace
**g':** more than 1 times in one file
***:** all files in directory

Good luck. I think the others are a bit harsh..

---

### Post by codemaniac on 2010-04-12
> I want something that can search within all the files.. bring up the files that has the code and then replace it..

notepad++ in windows is capable of doing this.. any one know how to do this in linux?

sed,awk,perl are the best text manipulators in *nix, no graphical tool can give you the hold better than these tools..To master them you have to practice them a lot..

---

### Post by faraz_k86 on 2010-04-12
> **nothingspecial said:**
> ```
regexxer - A visual search and replace tool
replaceit - quick, light and effective text replacement tool
rpl - intelligent recursive search/replace utility
searchmonkey - search files using regular expressions aiming to replace find/grep tools
```

results of apt-cache search

Never used any of them, but give one of them a go

Thanks a lot mate.. searchmonkey is exactly what i was looking for :)

---

### Post by faraz_k86 on 2010-04-12
> **Martje_001 said:**
> Try 'sed' on the commandline:
```
sed -i 's/text in file/replaced text/g'  *
```
**sed:** command used
**-i:** edit files in place
**'s:** replace
**g':** more than 1 times in one file
***:** all files in directory

Good luck. I think the others are a bit harsh..

Thankyou :)

---

### Post by HDave on 2011-10-26
Sorry to resurrect this old thread, but I have to say that regexxer totally rocks.  Best program I've seen in a long while.

---

### Post by Artif on 2012-03-16
> **nothingspecial said:**
> results of apt-cache search
Never used any of them, but give one of them a go

Tried to replace HTML code in CP1251 encoding:

[LIST]
[*]regexxer - failed to accept multi string text as a search expression.
[*]replaceit - it's description telling it is not able at all to work with multi lines text.
[*]rpl - failed to find text to be searched.
[*]searchmonkey - failed to find text to be searched.
[/LIST]

Sed? When parsing patterns with '!' (BASH is used), slashes and so on it may fail. When you need to work with fragments of HTML or another code, you must be an old shogun to be able to write fast a correct expression to be searched and another one to be substituted

When there is not too many files, seems it is good idea to open all the files in Bluefish/Geany/Eclipse/Notepad++ and do the job in several clicks. When you do not have too much files.

---

