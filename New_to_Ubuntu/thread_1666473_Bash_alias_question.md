---
title: "Bash alias question"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-13
Hi All,

I have several aliases for commands I often use.

Example
```
alias conkycalendar='conky -c ~/conkys/conkyrc2'
```

They all work fine.

I thought I'd put an alias in the .bash_aliases file to run a long command that shows reminders.

This is the command that works in the terminal.
```
remind -a '-kgmessage -buttons "OK:1" -default "OK" -center -font "serif 16" -fg "#46f" -bg white -wrap -title "Remember" %s &' ~/.reminders-timed
```

However if I set that with an alias of rt I get this:
```
 bash:  ~/.reminders-timed: No such file or directory
bash: alias: -buttons: not found
bash: alias: OK:1: not found
bash: alias: -default: not found
bash: alias: OK: not found
bash: alias: -center: not found
bash: alias: -font: not found
bash: alias: serif 16: not found
bash: alias: -fg: not found
bash: alias: #46f: not found
bash: alias: -bg: not found
bash: alias: white: not found
bash: alias: -wrap: not found
bash: alias: -title: not found
bash: alias: Remember: not found
bash: alias: %s: not found

```

Does anyone know why the command will run in the terminal, but not when I add an alias to it?

Update:  I solved the problem by saving the command as a Bash script and setting the alias to the script.  I still don't understand why that was necessary though.

---

### Post by Morrad on 2011-01-13
> **GrouchyGaijin said:**
> Hi All,
Update:  I solved the problem by saving the command as a Bash script and setting the alias to the script.  I still don't understand why that was necessary though.

If you were using the command exactly as you wrote it above, I'm guessing you had your alias line written as

```

alias = 'remind -a '-kgmessage -buttons "OK:1" -default "OK" -center -font "serif 16" -fg "#46f" -bg white -wrap -title "Remember" %s &' ~/.reminders-timed'
#       ^          ^
#       |          |
#       Problems start here.

```

As you can see, the single quotes ( ' ) are being closed prematurely.

Since the command you are using needs both single and double quotes, I think you're using the smart approach by just saving the command to a bash script file.

---

### Post by bodhi.zazen on 2011-01-13
That and IMO you should use the full path in scripts.

So rather then ~ or ./ use

/home/your_user/foo

Same with commands. 

Use /bin/bar not bar

For complex commands, rather then an alias, define a function.

---

### Post by GrouchyGaijin on 2011-01-14
> **bodhi.zazen said:**
> That and IMO you should use the full path in scripts.

So rather then ~ or ./ use

/home/your_user/foo

Same with commands. 

Use /bin/bar not bar

For complex commands, rather then an alias, define a function.
I'm kind of new to this.  Can you explain why it is better to use the full path?
I'm not sure what a function is either.  How would I make one and why is that better than an alias?

---

### Post by Vaphell on 2011-01-14
full path is foolproof and always works

short example of shell function
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html)
aliases work as a simple string substitution and are pretty much for oneliners only plus you get the parsing problems with ' and ", functions allow for more advanced constructs

---

### Post by bodhi.zazen on 2011-01-14
> **Vaphell said:**
> full path is foolproof and always works

short example of shell function
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html)
aliases work as a simple string substitution and are pretty much for oneliners only plus you get the parsing problems with ' and ", functions allow for more advanced constructs

Because variables such as ~ , ./ are inconsistent. What happens when user B runs the script ? What about when root runs it ? What happens when you call it from ~ ? What about from ~/Desktop ?

See also (bash) environmental variables.

It is much better to hard code.

If you call something more then once, use a variable

IPTABLES=/sbin/iptables

$IPTABLES ....
$IPTABLES ....

---

### Post by GrouchyGaijin on 2011-01-14
Thanks guys,

From now on I'll use the full path.
Since I'm the only one who uses my laptop I never even considered a "user B" running a script I have.

I read through the link that was posted about functions and honestly I found his explanation really confusing.  I did find another beginners guide to BASH online that seems to be a bit more clearly written.  (Perhaps the first guide was also clearly written for someone with more background knowledge than I have.)
:p

---

### Post by bodhi.zazen on 2011-01-14
> **GrouchyGaijin said:**
> Thanks guys,

From now on I'll use the full path.
Since I'm the only one who uses my laptop I never even considered a "user B" running a script I have.

I read through the link that was posted about functions and honestly I found his explanation really confusing.  I did find another beginners guide to BASH online that seems to be a bit more clearly written.  (Perhaps the first guide was also clearly written for someone with more background knowledge than I have.)
:p

Functions are nothing much more then complex aliases.

You define them in .bashrc, the syntax is a bit different, but basically they are short scripts.

---

### Post by sisco311 on 2011-01-14
> **GrouchyGaijin said:**
> 
I read through the link that was posted about functions and honestly I found his explanation really confusing.  I did find another beginners guide to BASH online that seems to be a bit more clearly written.  (Perhaps the first guide was also clearly written for someone with more background knowledge than I have.)
:p

That howto is outdated (last updated at Thu Jul 27 09:36:18 ART 2000).

There is another Bash howto on that site, the Advanced Bash-Scripting Guide. I wouldn't recommend it either.  It teaches you to write bugs, not scripts.

If you are looking for a good Bash howto, check out [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

