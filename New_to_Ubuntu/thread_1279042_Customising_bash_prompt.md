---
title: "Customising bash prompt"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by nnjond on 2009-09-30
Hi,

I'm swotting up on my bash skills. but can anyone save me some time by giving me the command to set my prompt in bold?

Thanks

---

### Post by unutbu on 2009-09-30
The trick is to surround the bash prompt code with
```

\[\033[01m\]  ...  \[\033[00m\]

```
For example, this shows you your current bash prompt code
```

% echo $PS1
\[\e]0;\u@\h: \w\a\]\t ${debian_chroot:+($debian_chroot)}\u@\h:\w%
```

and this redefines it (temporarily) to be bold:
```

% PS1='\[\033[01m\]\[\e]0;\u@\h: \w\a\]\t ${debian_chroot:+($debian_chroot)}\u@\h:\w%\[\033[00m\]'
```

---

### Post by nnjond on 2009-09-30
Thanks

---

### Post by slakkie on 2009-09-30
Hello,

function with all the color codes and a bit more:

```

set_ps1() {
  local NONE="\[\033[0m\]"    # unsets color to term's fg color

  # regular colors
  local K="\[\033[0;30m\]"    # black
  local R="\[\033[0;31m\]"    # red
  local G="\[\033[0;32m\]"    # green
  local Y="\[\033[0;33m\]"    # yellow
  local B="\[\033[0;34m\]"    # blue
  local M="\[\033[0;35m\]"    # magenta
  local C="\[\033[0;36m\]"    # cyan
  local W="\[\033[0;37m\]"    # white

  # empahsized (bolded) colors
  local EMK="\[\033[1;30m\]"
  local EMR="\[\033[1;31m\]"
  local EMG="\[\033[1;32m\]"
  local EMY="\[\033[1;33m\]"
  local EMB="\[\033[1;34m\]"
  local EMM="\[\033[1;35m\]"
  local EMC="\[\033[1;36m\]"
  local EMW="\[\033[1;37m\]"

  # background colors
  local BGK="\[\033[40m\]"
  local BGR="\[\033[41m\]"
  local BGG="\[\033[42m\]"
  local BGY="\[\033[43m\]"
  local BGB="\[\033[44m\]"
  local BGM="\[\033[45m\]"
  local BGC="\[\033[46m\]"
  local BGW="\[\033[47m\]"

  # without colors: PS1="[\u@\h \${NEW_PWD}]\\$ "
  # extra backslash in front of \$ to make bash colorize the prompt
  cur_tty="$(tty)" ; cur_tty="${cur_tty:5}"   # The tty we are working on
  last_exit="\$?"          # Exit code of the command executed from the prompt..
  if [ $UID -eq 0 ] ; then # Check for root
    UBC=$BGB
    UC=$EMR
    TERM_STRING='#'
  else # Otherwise..
    UBC=$BGB
    UC=$EMG
    TERM_STRING='$'
  fi
  export PS1="${UBC}${EMW}\t $cur_tty $last_exit${NONE} ${UC}\u@\h:\w${NONE}${TERM_STRING} "
}

```

---

