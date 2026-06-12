---
title: "reduce length of command line"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by shaheru on 2009-07-24
Hello,
I would like to find a way to reduce the length of the command line 

from:

valerio@valerio:~/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC$ cd test-runs/gfortran/TEST_DIR/

to :

valerio@valerio:~/TEST_DIR/


I would be happy to have any suggestions!

---

### Post by lavinog on 2009-07-24
```
PS1='[ \u@\h:\W ]'
```
will change it to
[ user@host:currentdir ]

---

### Post by sisco311 on 2009-07-24
edit ~/.bashrc
```
gedit ~/.bashrc
```
replace the lowercase w with an uppercase W in the PS1=`blah blah...` lines:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\[COLOR="Red"]w[/COLOR]\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="#ff0000"]w[/COLOR]\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \[COLOR="Red"]w[/COLOR]\a\]$PS1"
    ;;
*)
    ;;
esac


```

---

### Post by Hospadar on 2009-07-24
Your prompt gets set up in your ~/.bashrc

you'll see something like this: ```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```
Here's some fuller info: [http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

but it short, replace \w with \W

---

### Post by shaheru on 2009-07-24
Thanks for replies,
the one of Hospadar fit well with what I was looking for,
changing the .baschrc file.

---

### Post by Cheesemill on 2009-07-24
Take a look here for more information than you could ever need about bash prompt customisation.

[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

---

