---
title: "terminal shortcuts?"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by fremantle on 2011-06-14
is there any way to set up terminal short cuts, for example, i use **sudo add-apt-repository** alot, so i let up a short command to simplify using it, like i make **addrepo** to execute the full **add-apt-repository** command. u feel me?

---

### Post by fremantle on 2011-06-14
just discovered the magic of bashrc. solved.

---

### Post by ajgreeny on 2011-06-14
There is a thread on useful aliases, if I remember correctly.

Here are mine, not in .bashrc, but to keep things more easily findable in .bash_aliases.  Some are now redundant, but I have kept them, just in case:-

alias addppa='sudo add-apt-repository'
alias am='alsamixer'
alias blk='sudo blkid'
alias cleanhistory='grep -v ^q .bash_history > .bash_history2 && mv .bash_history .bash_historybak && mv .bash_history2 .bash_history'
alias cp='cp -i'
alias cron='gedit Quicknotes/Cron_Commands.txt & crontab -e'
alias db='sudo updatedb'
alias df='df -hT'
alias dl='vnstat -d'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias dll='vnstat -l'
alias egrep='egrep --color=auto'
alias fd+='mount /media/floppy'
alias fd-='umount /media/floppy'
alias fgrep='fgrep --color=auto'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > $(date +%F-%I%M)hw.html'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -lh'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'
alias mv='mv -i'
alias q='exit'
alias rm='rm -i'
alias scan='sudo tune2fs /dev/sda1 -l'
alias scanhome='sudo tune2fs /dev/sda2 -l'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='mbmon -c 4 && hddtemp /dev/sda /dev/sdb'
alias version='uname -a && lsb_release -a'
alias xorg='cat /etc/X11/xorg.conf'

---

### Post by fremantle on 2011-06-14
> **ajgreeny said:**
> There is a thread on useful aliases, if I remember correctly.

Here are mine, not in .bashrc, but to keep things more easily findable in .bash_aliases.  Some are now redundant, but I have kept them, just in case:-

alias addppa='sudo add-apt-repository'
alias am='alsamixer'
alias blk='sudo blkid'
alias cleanhistory='grep -v ^q .bash_history > .bash_history2 && mv .bash_history .bash_historybak && mv .bash_history2 .bash_history'
alias cp='cp -i'
alias cron='gedit Quicknotes/Cron_Commands.txt & crontab -e'
alias db='sudo updatedb'
alias df='df -hT'
alias dl='vnstat -d'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias dll='vnstat -l'
alias egrep='egrep --color=auto'
alias fd+='mount /media/floppy'
alias fd-='umount /media/floppy'
alias fgrep='fgrep --color=auto'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipg='get_iplayer -g'
alias gipr='get_iplayer --type radio'
alias grep='grep --color=auto'
alias hw='sudo lshw -html > $(date +%F-%I%M)hw.html'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -lh'
alias ls='ls --color=auto'
alias menu='grep menuentry /boot/grub/grub.cfg'
alias mv='mv -i'
alias q='exit'
alias rm='rm -i'
alias scan='sudo tune2fs /dev/sda1 -l'
alias scanhome='sudo tune2fs /dev/sda2 -l'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='mbmon -c 4 && hddtemp /dev/sda /dev/sdb'
alias version='uname -a && lsb_release -a'
alias xorg='cat /etc/X11/xorg.conf'

nice!
im using,

ins rmv armv addrep upd upg clean

---

