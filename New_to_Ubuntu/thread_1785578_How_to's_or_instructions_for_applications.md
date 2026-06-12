---
title: "How to's or instructions for applications?"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-18
Okay this is a newbie question for open source and linux software applications.  Is there a hidden place or something to find instructions or how-to-use information?  I suspect for some applications there isn't any provided, but how is it provided if it does exist?

I know some applications have web or wiki pages, but not many, and even then the basic op instructions are pretty lean or non-existent.  Is there a system file someplace for README files that provide that?  

I know that a lot of folks never open instructions....but some of us do.  I also know that it is really difficult to WRITE good INSTRUCTIONS, and I suspect that it isn't a big skill with most developers, and something they just don't LIKE to do.  Since there is no MARKETING per say with open source there isn't someone else coming along behind to do this step.

But anyway, thought I would check....I like to have a little reference to at least get me started or help me out when I'm stuck (the forums are great, but for all those apps!)

---

### Post by User3k on 2011-06-18
You mean something like this?

[http://tldp.org/](http://tldp.org/)

---

### Post by oldos2er on 2011-06-18
The **man** and **info** commands provide much of the documentation for Linux programs. Gnome app docs are here: [http://library.gnome.org/users/](http://library.gnome.org/users/)
KDE app docs here: [http://docs.kde.org/](http://docs.kde.org/)
And of course [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by inameiname on 2011-06-18
The manpages are the way to go for lots of useful info for whatever application. 

And if you'd like, here are two functions which make it easier to read over and over certain packages desired. Just add these to your ~/.bashrc file.:

```

##################################################
# Manpage to ... document             
##################################################

###### example:    man2pdf wipe    =    wipe.pdf
# copyright 2007 - 2010 Christopher Bratusek
function man2pdf()
{
    case $1 in
        *help | "" )
            echo -e "\nUsage:"
            echo -e    "\nman2pdf | <manualpage> [generate a pdf from <manualpage>]\n"
            tput sgr0
        ;;
        * )
            check_opt ps2pdf man2pdf
            if [[ $? != "1"  && $1 ]]; then
                man -t $1 | ps2pdf - >$1.pdf
            else    echo "No manpage given."
            fi
        ;;
    esac
}



###### example:    man2text wipe    =    wipe.txt
function man2text()
{
man "$1" | col -b > ~/man_"$1".txt
}

```

---

### Post by smcrossman on 2011-06-18
I am so glad I asked.  I've seen man pages referred to a lot (and I've used a few) but it will be a new habit to develop and I'm never quite sure exactly what to use for the command/name part...but I'll learn it!

The web site looked great....I would have never guessed that such a thing was out there.  I will need to spend some time exploring it to see how useful it can be! 

Thanks!

Now I'm going to mark this solved but I am still open to other resources if anyone knows of any!  ;)

---

### Post by AlphaLexman on 2011-06-18
> **inameiname said:**
> ```

            echo -e "\n[COLOR="Red"]${ewhite}[/COLOR]Usage:"
            echo -e    "\n[COLOR="red"]${eorange}[/COLOR]man2pdf[COLOR="red"]${ewhite}[/COLOR] |[COLOR="red"]${egreen}[/COLOR] <manualpage>[COLOR="red"]${eiceblue}[/COLOR] [generate a pdf from <manualpage>]\n"


```
@ inameiname: Although your intentions are good, you have [COLOR="red"]${color_variables}[/COLOR] that **NOT** every user may have... It may be best to _delete_ those variables from your code before posting!

Regards.

---

### Post by inameiname on 2011-06-18
Thanks for the tip. I hadn't noticed that. It's not my code, just one I found around from a Mr. Christopher Bratusek. It always worked for me without an issue inside my 'Ultimate Bashrc' ([http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746)) so I just copied/pasted it here.

Anyway, thanks. I may have to change it on my .bashrc too for those who may find trouble using it.

---

### Post by oldos2er on 2011-06-18
> **smcrossman said:**
> I am so glad I asked.  I've seen man pages referred to a lot (and I've used a few) but it will be a new habit to develop and I'm never quite sure exactly what to use for the command/name part...but I'll learn it!;)

Usually you just use the app name, e.g. **man firefox**. If you don't know the name, the **apropos** command should help you find it, e.g. **apropos browser**.

**q** exits the man pages.

---

### Post by cmcanulty on 2011-06-18
Check these links out
[http://ubuntuforums.org/showthread.php?t=801404]("http://ubuntuforums.org/showthread.php?t=801404")

---

