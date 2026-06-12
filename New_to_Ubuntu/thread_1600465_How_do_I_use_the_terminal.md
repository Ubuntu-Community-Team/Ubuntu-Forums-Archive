---
title: "How do I use the terminal?"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-10-19
Hello everyone,
I am very new to Ubuntu and I started using computers JUST after MS DOS. Therefore, I'm not very well versed in command lines. 

I would REALLY like to utilize the terminal, as it seems like a super powerful tool. 

Here are my questions:

1. What would be some situations where it would make the most sense to use the terminal, rather than the GUI?

2. What are a few commands that I can't live without and will be able to use on a regular basis?

3. Eventually, I would not just like to know specific commands but be able to speak the terminal's language... sort of making up my own, within the confines of the language. Is this possible? How can I do this?

Please let me know the answers to these questions and any others. Thanks!

---

### Post by xXNI4NI on 2010-10-19
Check out: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

Basically an introductory article to the terminal with some other useful links that can take you deeper into the terminal.

---

### Post by ndefontenay on 2010-10-19
With Linux the first reason is:
1) When getting help from the forum
Instead of saying go to here, click there, look for this then do that. 

You can simply say: Copy this and paste it into your terminal

2) If you need to do a task repetitively, you could in one command prefix say the 1000 pictures you got in a folder with your name in front.

3) If it gets more complex than 2) you can stick it in a script.

---

### Post by mastablasta on 2010-10-19
here is an interesting free e-book if you are up for some reading:
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
 
basic commands are nicelly explained in the first chapters followed by advanced commands and programming to put the cherry on top of the cream.

---

### Post by jmszr on 2010-10-19
Ranger_Joe,

Here are a couple of posts that cover the basics of terminal use from the beginner's standpoint: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) and: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) .

Hope that helps.

---

### Post by fancypiper on 2010-10-19
The command line is the lowest common denominator of all Linux distros, so it makes sense to understand bash (Bourne again shell). You can create aliases to define your own commands for stuff that is difficult to remember.
```
## tinwhistle box ~/.bash_aliases file for user phil
# User specific aliases and functions

# Clear the terminal
alias cls='clear'

# Start X server
alias x='startx'

# Change bash prompt. See the article
# http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/
export PS1='\d \@ \[\e[32;1m\]\u\[\e[34;1m\]@\[\e[36;1m\]\H \[\e[34;1m\]\w\[\e[32;1m\] $ \[\e[0m\]'

# Keep 1000 lines in .bash_history (default is 500)
export HISTSIZE=1000
export HISTFILESIZE=1000

#Stop bash from caching duplicate lines.
HISTCONTROL=ignoredups

# Disk free in human terms
alias df='df -h'

# List paths
alias path='echo -e ${PATH//:/\\n}'

# Encode wav files to flac and delete the wav file
alias zipwavd='flac -V --best --delete-input-file *.wav'

# Encode wav files to flac and keep the wav file
alias zipwav='flac -V --best *.wav'

# Decode flac files to wav format
alias uzipwav='flac -d -V *.flac'

# Encode wav to ogg
# alias oggem=oggenc -n *.wav -o *.ogg

# Allow local users to use my X session
# xhost +local:

# I can't remember the new gnome command!
alias gtop='/usr/bin/gnome-system-monitor'

# Alter the ls command
alias ll='ls --color --time-style="+%b %d %Y %H:%M"'
alias ls='ls -ac'
alias lls='ls -lac'
alias la="ls --color -lAGbh --time-style='+%b %d %Y %H:%M'"

# Set background in Fluxbox
# alias bg='fbsetbg -a /home/phil/Pictures/kells/kelljesusarrest.gif'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol114rArrestOfChrist.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/KellsFol007vMadonnaChild.jpg'
# alias bg='fbsetbg -a /home/phil/Pictures/kells/4evangelists.jpg'
alias bg='fbsetbg -a /home/phil/Pictures/Family/jack_phil_40gs.jpg'

# Become system administrator
alias god='sudo -i'
alias root='sudo -i'

# Because less is more and more is less
alias more='less'

# xterm
# alias xterm='xterm -bg black -fg green'

# Launch links or w3m with my linux links page
alias web='links2 -g /home/phil/bookmarks.html'
alias wweb='w3mmee /home/phil/bookmarks.html'

# For nano editor
alias nano='nano -w'

# Start gkrellm after stopping it in x
alias gkrellm='gkrellm -w &'

# Kill mplayer
alias kmp='killall -9 mplayer & killall -9 gnome-mplayer'
```

[Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)

[LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz)

---

### Post by Ranger_Joe on 2010-10-19
Mastablasta, you rock. This e-book is awesome. I'm gonna be a terminal using fool very soon. SOLVED!

---

### Post by JKyleOKC on 2010-10-19
I think fancypiper left out a few of what I think are the most important aliases on my system:

```
alias rm=rm -i
alias mv=mv -i
```

These force me to confirm any "remove" or "move" command that I issue, thus giving me a chance to double-check that it's going to do what I intended, before it's too late.

Incidentally, good to see you diving in! How's the new baby doing?

---

### Post by Ranger_Joe on 2010-10-19
Jkyle, great to hear from you man. I'll take note of those commands. I am knee deep in these forums and loving it. Baby is great.

---

