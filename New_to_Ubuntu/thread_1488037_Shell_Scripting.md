---
title: "Shell Scripting"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Lolpanda on 2010-05-19
Right now I have a script that installs a set of packages to a brand new installation, codecs, wine, docky, a few other misc things. This was basically done because of me constantly switching around distro's or re-installing ubuntu for a multitude of reasons and wanting to streamline getting the OS back up and running. It worked great, until a few friends here liked my set up and wanted to copy it. 

The issue is, some like docky, some like AWN, some run 32-bit, some run 64-bit. Some want wine, some don't want wine. Instead of telling them "Just tweak the script" and leaving them out to dry like that, I was hoping if someone could direct me to some reading, or outright explain how to add different prompts and have the script store them for later use. So that if I ask "Would you like Docky or AWN?" if they reply "AWN" then when everything is all said and done, the command to install AWN will be executed without Docky being installed as well. 


A note: if you want to explain it, give a coding example, don't just say "oh well just make a variable and tell it if... then ... " I work, and learn best, if I have an example to work off of and see how everything comes together.

---

### Post by Darkness Des on 2010-05-19
I'd be glad to help. [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

That's where I learned shell scripting. It also takes a while to find anything specific as they lack a search function, so here are some examples:

```

echo -n "Would you like AWN or Docky > "
read dock

function dock
{
if [ dock = AWN ]; then
    sudo aptitude install avant-window-navigator
elif [ dock = Docky ]; then
    sudo aptitude install docky
fi
}

$(dock)

```

That would use a function to read what they typed, then proceed to execute it. I have a script for making HTML Pages that has some questions when run that requires user input similar to that. If you want to view several possibilities for having question/answer situations like that, the script is available at
[http://darknessdes.ucoz.com/Projects/make_page/make_page.sh](http://darknessdes.ucoz.com/Projects/make_page/make_page.sh)

And you are free to download it without registration/surveys/interaction/anything else. I hate sites that do that.

---

### Post by bodhi.zazen on 2010-05-19
My only 2c would be to not use doc as both teh name of the variable you are reading and the function. With such a short script it does not matter, but with longer scripts it makes it hard to read.

IMO commenting a script is essential, one should be able to read an understand the variables and functions. It takes a little effort to do so, but it really helps later when you need to modify the script.

---

### Post by Lolpanda on 2010-05-19
A thank you to both of you, Darkness & Bodhi. I'll be sure to check out both links, Darkness. And thank you for the reminder on commenting Bodhi. I normally don't comment my scripts just because I usually remember what they do, though it is a very valid point you make.

Only other thing I could think of with this script, (I come from a VB.net, Batch, and QBasic background) Is if there was some way to slowly add the commands to the final line. Meaning: if they would install nothing the line would look like

```
aptitude install
```

if they wanted docky the line would look like

```
aptitude install docky
```

if they wanted docky and wine it would look like

```
aptitude install docky wine1.2
```

and keep having that line updating based on their answers until the very last question was answered, at which point it would execute and everything would be handled at once instead of in 20 different

```
aptitude install ....
```

---

### Post by Lolpanda on 2010-05-19
May have just found the answer to my own question, with the " >> " command, to append the line. If anyone can confirm that this will work, or explain why not, or any other helpful hints. I'd love to hear it.

---

### Post by DarkestRitual on 2010-05-19
> **Darkness Des said:**
> I'd be glad to help. [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

That's where I learned shell scripting. It also takes a while to find anything specific as they lack a search function, so here are some examples:

```

echo -n "Would you like AWN or Docky > "
read dock

function dock
{
if [ dock = AWN ]; then
    sudo aptitude install avant-window-navigator
elif [ dock = Docky ]; then
    sudo aptitude install docky
fi
}

$(dock)

```

That would use a function to read what they typed, then proceed to execute it. I have a script for making HTML Pages that has some questions when run that requires user input similar to that. If you want to view several possibilities for having question/answer situations like that, the script is available at
[http://darknessdes.ucoz.com/Projects/make_page/make_page.sh](http://darknessdes.ucoz.com/Projects/make_page/make_page.sh)

And you are free to download it without registration/surveys/interaction/anything else. I hate sites that do that.

Holy thank you... I've been looking for something like this forever. Just what the doctor ordered, and I wasn't even expecting to find anything this sweet. :)

---

