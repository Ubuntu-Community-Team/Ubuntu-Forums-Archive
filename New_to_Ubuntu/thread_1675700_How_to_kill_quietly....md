---
title: "How to kill quietly..."
date: 2011-01-26
forum: New to Ubuntu
---

### Post by daggoth8 on 2011-01-26
I would like to know how to kill a background process quietly, without having 
any messages. Coz whenever I invoke 'kill' from within a script, I'd like
it to be free of output... 

But as you can see in my example below, I have unsuccessfully tried to suppress
the output of the kill command. I can only guess that the "[1]+ Terminate.."
message does not come directly from the 'kill' command, but possibly indirectly
from the bash shell and job control instead. If so, then can a 'shopt' 
command be used to quieten messages from job control?  

Thanks.

root:~# sleep 100 &
[1] 2866
root:~# kill $! 1>&2 2>/dev/null
[1]+  Terminated              sleep 100
root:~# 
root:~# 
root:~# shopt -p
shopt -u autocd
shopt -u cdable_vars
shopt -u cdspell
shopt -u checkhash
shopt -u checkjobs
shopt -s checkwinsize
shopt -s cmdhist
shopt -u compat31
shopt -u compat32
shopt -u compat40
shopt -u dirspell
shopt -u dotglob
shopt -u execfail
shopt -s expand_aliases
shopt -u extdebug
shopt -u extglob
shopt -s extquote
shopt -u failglob
shopt -s force_fignore
shopt -u globstar
shopt -u gnu_errfmt
shopt -s histappend
shopt -u histreedit
shopt -u histverify
shopt -s hostcomplete
shopt -u huponexit
shopt -s interactive_comments
shopt -u lithist
shopt -s login_shell
shopt -u mailwarn
shopt -u no_empty_cmd_completion
shopt -u nocaseglob
shopt -u nocasematch
shopt -u nullglob
shopt -s progcomp
shopt -s promptvars
shopt -u restricted_shell
shopt -u shift_verbose
shopt -s sourcepath
shopt -u xpg_echo
root:~#

---

