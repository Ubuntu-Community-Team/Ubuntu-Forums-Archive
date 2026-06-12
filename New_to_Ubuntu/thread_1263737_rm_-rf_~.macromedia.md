---
title: "rm -rf ~/.macromedia"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by matchstich on 2009-09-11
hi,

 i went  here

[http://ubuntuforums.org/showthread.php?t=1260891&highlight=flash+cookies](http://ubuntuforums.org/showthread.php?t=1260891&highlight=flash+cookies)

and there was a link in there 

[http://www.linuxplanet.com/linuxplanet/reports/6711/2/](http://www.linuxplanet.com/linuxplanet/reports/6711/2/)

that better explained how to do it.

cept, from day one since i joined this forum  i have been  warned about doing any 

rm commands as they may be harmful to my system

just wanted to check and see if this is ok to do.

am trying to guard my system against and remove all flash cookies  on it.

i have installed better privacy but to my knowledge it only removes cookies that i pick up along the way and does not remove cookies that may be already in my system


thanks

am running ubuntu 9.04,  i clicked the wrong one do not have kubuntu and do not know how to change that.

---

### Post by sisco311 on 2009-09-11
It's perfectly safe to run that command, it will delete the .macromedia directory from your home directory. 

But you can use your file manager as well. You may need to press Ctrl+H to list the hidden files.

---

### Post by Penguin Guy on 2009-09-11
rm deletes files and folders, it is perfectly safe, just make sure that it's deleting the file you want it to delete: [COLOR="Green"]~/.macromedia[/COLOR] = [COLOR="Green"]/home/*username*/.macromedia[/COLOR]. Never use rm on / (whole system) or ~ (home).

---

### Post by matchstich on 2009-09-11
well, what i want to is what is explained in the second link.  it is supposed to for removing  existing cookies and sending future cookies to no where.  if i read it right.


thanks

---

### Post by Gen2ly on 2009-09-11
Well, you can delete the directory but it will pop up again likely when you use flash (depending on how flash is used on the site).  You're right though.  Flash is !@# !@#$ 12#$ and a whole bunch of bad news.  Flash does have an exploit that various clients and myself have seen been exploited to gain at least partial access to the system (maybe more).  I know for sure that through flash someone was able to hack the chrome folder in my firefox preferences.  I haven't been real happy with Adobe for this especially since they don't seem real concerned about security.  Flash 10 alpha for 64 bit was released almost 10 months ago and we have yet to see an update.  What I do to help protect my system and still use flash is redirect ~/.macromedia and ~/.adobe to /dev/null.  I wrote a script that toggles on/off this behavior because some sites just require flash (espn, cbs...) that I use regular.  Here's the script:

```
#!/bin/bash
# flashprotect - redirect flash config files to dev null

# Text color variables
TXTBLD=$(tput bold)     # Bold
TXTUND=$(tput sgr 0 1)  # Underline
TXTRED=$(tput setaf 1)  # Red
TXTGRN=$(tput setaf 2)  # Green
TXTYLW=$(tput setaf 3)  # Yellow
TXTBLU=$(tput setaf 4)  # Blue
TXTPUR=$(tput setaf 5)  # Purple
TXTCYN=$(tput setaf 6)  # Cyan
TXTWHT=$(tput setaf 7)  # White
TXTRST=$(tput sgr0)     # Reset

# Create (or restore orginial) directories if they don't exist
if [ ! -d ~/.macromedia ] && [ ! -L ~/.macromedia ]; then
  if [ ! -d ~/.macromedia.bck ]; then
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}No ~/.macromedia backup folder, creating ~/.macromedia folder"
  mkdir ~/.macromedia; else
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}~/.macromedia.bck found, restoring"
  mv ~/.macromedia.bck ~/.macromedia
  fi
fi

if [ ! -d ~/.adobe ] && [ ! -L ~/.adobe ]; then
  if [ ! -d ~/.adobe.bck ]; then
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}No ~/.adobe backup folder, creating ~/.macromedia folder"
  mkdir ~/.adobe; else
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}~/.adobe.bck found, restoring"
  mv ~/.adobe.bck ~/.adobe
  fi
fi

# Do ~/.macromedia and ~/.adobe match (link or dir)?  If no then fix.
if [ -d ~/.macromedia ] && [ -L ~/.adobe ]; then
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}~/.macromedia and ~/.adobe aren't both directories or links, fixing."
  rm -f ~/.adobe
  if [ -d ~/.adobe.bck ]; then
    mv ~/.adobe.bck ~/.adobe; else
    mkdir ~/.adobe
  fi
fi

if [ -d ~/.adobe ] && [ -L ~/.macromedia ]; then
  echo "${TXTBLD}${TXTGRN} * ${TXTRST}~/.macromedia and ~/.adobe aren't both directories or links, fixing."
  rm -f ~/.macromedia
  if [ -d ~/.macromedia.bck ]; then
    mv ~/.macromedia.bck ~/.macromedia; else
    mkdir ~/.macromedia
  fi
fi

# Toggle /dev/null and original directories
if [ -d ~/.macromedia ] && [ -d ~/.adobe ]; then
  mv ~/.macromedia ~/.macromedia.bck
  mv ~/.adobe ~/.adobe.bck
  ln -sf /dev/null ~/.macromedia
  ln -sf /dev/null ~/.adobe
  echo "${TXTBLD}${TXTGRN} * ${TXTRST} Blackholed"; else
  rm ~/.macromedia
  rm ~/.adobe
  mv ~/.macromedia.bck ~/.macromedia
  mv ~/.adobe.bck ~/.adobe
  echo "${TXTBLD}${TXTGRN} * ${TXTRST} Restored"
fi
```

---

### Post by mc4man on 2009-09-11
The script method of Gen2ly seems to be a better option than always redirecting.
 Very nice done

---

### Post by Irvine_himself on 2009-09-11
As was pointed out in the post, (by a number of posters,) if you don't want to take any risks, there is a perfectly good Firefox add-on called "Better Privacy" it works fine and allows you to keep the cookies for a short time.

This is important since the Flash cookies can also hold useful session information about settings and what not. Sending them to directly to nul is a bit like trying to browse while rejecting all cookies......   Possible but not practical.

Ps 

Better Privacy does remove all cookies, when you click on 

Tools >> Add-ons >> Better Privacy >> Options

You have an interface which show s all cookies currently stored and the option to immediately delete them, (including settimgs.sol)

---

### Post by matchstich on 2009-09-11
thanks every one.. as for the script,  i do not know how implement it.

but as long as i can go in and delete , that will work.

appreciate it .

---

### Post by Gen2ly on 2009-09-12
> **Irvine_himself said:**
> As was pointed out in the post, (by a number of posters,) if you don't want to take any risks, there is a perfectly good Firefox add-on called "Better Privacy" it works fine and allows you to keep the cookies for a short time.

This is important since the Flash cookies can also hold useful session information about settings and what not. Sending them to directly to nul is a bit like trying to browse while rejecting all cookies......   Possible but not practical.

Ps 

Better Privacy does remove all cookies, when you click on 

Tools >> Add-ons >> Better Privacy >> Options

You have an interface which show s all cookies currently stored and the option to immediately delete them, (including settimgs.sol)

Yes, this is true, Irvine_himself.  But Better Privacy only deletes Flash cookies on exit (at least, from the last time I ran it about a month ago).

> **matchstich said:**
> thanks every one.. as for the script,  i do not know how implement it.

but as long as i can go in and delete , that will work.

appreciate it .

If you want to be able to run scripts (scripts are handy text files that can perform multiple commands, specialized-commands...), you can look at [this page]("http://linuxtidbits.wordpress.com/2009/08/05/week-of-bash-scripts-newx-and-bgcmd/") if you want.

---

### Post by Irvine_himself on 2009-09-12
No, you can set it to delete any cookie that has no activity for a user defined time. Also, it blocks ping back tracking while it exists, you can disable Dom storage, and of course, you can create exceptions. 

Personally I think it is brilliant, I wish my traditional cookie manager was as versatile.

---

### Post by matchstich on 2009-09-12
thanks again for the info, gave me a lot of reading to do.  and hopefully i will finger it out and get something done.

---

