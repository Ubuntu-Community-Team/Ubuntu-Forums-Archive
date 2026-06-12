---
title: "Some beginner ssh issues/questions"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by employeeno5 on 2008-11-22
Hi there,

So I've never tried using secure shell before and my networking knowledge is pretty limited. 

First off, let me explain what I'm attempting to do and then I'll let you know where I'm running into trouble. 

I've got a desktop running 8.10 with a 40GB music collection on it. I recently got a Dell Mini 9 with the custom factory install of 8.04. What I was hoping to do was establish an ssh connection between the two and remotely mount my Music folder from the desktop onto the Mini. So far I'm just trying this over the wireless LAN here in the house. 

Now I've found numerous guides both here and elsewhere on the net describing how to mount remote folders with ssh. I'm hoping to eventually make this automated, so that I have this folder anywhere I'm connected to the net. 

However, before I can even find out if I'm going to have any problems there, I'm still unable to do a regular ssh connection from my Mini to my desktop here at home.

So I'm here on the Mini and I go:

```
sudo ssh broderick@192.168.0.16
```

Now, I realize that this is just the local ip (don't know the correct terminology) and that this won't work once I venture outside of my LAN. However, I figured I'd cross that bridge when I come to it and just try out an ssh connection of any sort first.

So, ssh gives me the line:

```
The authenticity of host '192.168.0.16 (192.168.0.16)' can't be established.
RSA key fingerprint is 92:f0:10:23:8e:04:85:2b:bb:0c:73:a5:83:0f:e3:f0.
Are you sure you want to continue connecting (yes/no)?
```

I tell it yes and it says Warning: and tells me it's adding the computer to list of known hosts. Then it asks me for my desktops password.

All of this is normal to my current understanding. However, after giving it the password, I just a get a blinking cursor forever, like it's still thinking about something.

I get no further output, even if I wait over an hour. The only way to cease this blank, blinking cursor is to just close down the terminal. 

What am I missing? Why might it not be connecting?

If anyone could help me get past this first step that would huge. Any further advice for down the line might be nice too, but really, just establishing a basic connection would be a great start.

I'm guessing this has something to do with my wirless LAN, but really I don't know, and if it is, I wouldn't know what the problem is or what to do.

I'm sorry if this seems awfully noobish, but I've really been searching around and trying this off and on for over a week. All the guides I read seem to say I should be connecting now and I haven't seemed to have missed any steps.

Whew! Sorry for being so long winded. If anyone has any advice or guidance and troubleshooting suggestions, please let me know.

Many thanks!
Broderick

---

### Post by Iowan on 2008-11-22
The blinking cursor seems normal - I get that when connection to another machine... but I _do_ usually get the prompt from machine I've ssh'ed into.

Then again, I've never done it on wireless.

---

### Post by ITAndrew on 2008-11-22
I have had this problem before, but it only happens when the CPU load is high or if the PC freezes/ hard locks on login. So far you have done everything right.

FYI, you can view the authorisation log which is located at /var/log/auth.log which also may provide some insight.

---

### Post by jpkotta on 2008-11-22
Have you modified your ~/.bashrc or ~/.profile at all?  If either one includes a command that outputs something, ssh might have trouble.  Also try ssh on the computer your trying to ssh to.  E.g. physically log into the .16 machine and do ```
ssh localhost
```

---

### Post by employeeno5 on 2008-11-22
> I have had this problem before, but it only happens when the CPU load is high or if the PC freezes/ hard locks on login. So far you have done everything right.

I've got the blinking cursor as I type and processor is currently at 47% on my mini and 11% on my desktop. 

I've had no freezing issues on either. 

Ugh.

> Have you modified your ~/.bashrc or ~/.profile at all? If either one includes a command that outputs something, ssh might have trouble. Also try ssh on the computer your trying to ssh to. E.g. physically log into the .16 machine and do

I can connect the .16 machine to itself without issue. However, yes I have altered ~/.bashrc

I don't know if it "includes a command that outputs something", I only altered it to change the appearance of the prompt to reflect just the current working directory and I added a "!" just because I like it. Here's my .bashrc below though if you want to check it out.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_colored_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='\[\e[1;32m\][\w]\[\e[m\]! '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

#my personal aliases below
alias desktop='cd ~/Desktop'
alias home='cd ~'
alias rm='rm -i'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```


Also, for some further info, in my efforts to get this going I currently have no firewall enabled on my machines or the router, so that's not causing the issue. 


Another questions: Right now I'm trying to connect the address on the LAN. How would I go about this if I were trying to do this from an outside source? Let's say I was out and about in the world and wanted to ssh in. How would I designate connecting to my desktop (.16) after reaching my router's IP? 

Might it be helpful to try connecting that way? Trying to connect as if I wasn't on the same LAN as my destination?

---

### Post by employeeno5 on 2008-11-22
Quick update: I restored my custom ~/.bashrc to it's original file and still had no results, so I don't think that's an issue in this case.

---

### Post by jpkotta on 2008-11-22
Your ~/.bashrc looks OK.  I just remember I used to have fortune in my ~/.bashrc and it messed up ssh.  And I realize now that I moved it to ~/.bash_profile, and that makes things OK.

Did you try the local ssh?

To access the machine from the internet, you need to enable port forwarding on your router.  I like to pick a high port number for the incoming (from internet) traffic.  E.g. forward internet traffic on port 23456 to port 22 on 192.168.0.16.  Then set up a dynamic dns service so you don't have to figure out what your internet ip is.  I use no-ip.com.

---

### Post by employeeno5 on 2008-11-23
> Your ~/.bashrc looks OK. I just remember I used to have fortune in my ~/.bashrc and it messed up ssh. And I realize now that I moved it to ~/.bash_profile, and that makes things OK.

Did you try the local ssh?

To access the machine from the internet, you need to enable port forwarding on your router. I like to pick a high port number for the incoming (from internet) traffic. E.g. forward internet traffic on port 23456 to port 22 on 192.168.0.16. Then set up a dynamic dns service so you don't have to figure out what your internet ip is. I use no-ip.com.


Yes, I tried local ssh and it connected properly.

Ok. So regarding port forwarding, here I need a little bit of education. I believe I understand what you asking me to do and why, and my router, like most, has a handy configuration tool I can open in my browser.

However, when I go to the port forwarding section, it doesn't seem to give me an option for or make clear what I'm forwarding to and where. 

I've attached a screen shot.

You see, it lets me specify a port, but that doesn't seem to allow me to tell it where I want to forward that port to. Or do I have that backwards? I thought that perhaps the "end" section would be where I could put the 22 to send it to ssh, but it says that it needs to be a higher number (my original assumption). I'm little lost here on the port forwarding thing.

Thanks for the tip on No-IP by the way. I will surely have use for it, if I can ever get this working. Looks very handy.

---

### Post by jpkotta on 2008-11-23
Check the documentation for the router, but it sounds like you don't get to specify a different forwarded port.  In that case, you'll have to make ssh listen on whatever port you use in /etc/ssh/sshd_config.

So local ssh works then.  Try a remote ssh with verbose output.
```
ssh -v user@remote
```

---

### Post by employeeno5 on 2008-11-23
Cool. Thanks for the port forwarding heads-up.

Ok, so we're back on the Mini now trying to ssh the desktop (.16). Both computers ssh locally fine.

Being verbose this time we get:

```
broderick@mini:~$ ssh -v broderick@192.168.0.16
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/broderick/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.16 [192.168.0.16] port 22.
debug1: Connection established.
debug1: identity file /home/broderick/.ssh/identity type -1
debug1: identity file /home/broderick/.ssh/id_rsa type -1
debug1: identity file /home/broderick/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.16' is known and matches the RSA host key.
debug1: Found key in /home/broderick/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/broderick/.ssh/identity
debug1: Trying private key: /home/broderick/.ssh/id_rsa
debug1: Trying private key: /home/broderick/.ssh/id_dsa
debug1: Next authentication method: password
broderick@192.168.0.16's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8

```

Where that ends we have the blinking cursor forever. So it looks like I'm connecting and the password is going through, but I'm left with this non-responsive cursor anyways rather than a usable prompt.

---

### Post by lemuriaX on 2008-11-23
Hi and greetings to a fellow lemur :)
This might not be on track but am curious, do you have a way to test connecting via SSH with a wired LAN just in case the problem is related to your wireless somehow?

---

### Post by employeeno5 on 2008-11-23
> Hi and greetings to a fellow lemur
This might not be on track but am curious, do you have a way to test connecting via SSH with a wired LAN just in case the problem is related to your wireless somehow?

Greetings to you too! Huzzah! 

Unfortunately, no I do not have a way of doing that at home. My router only has one output for an ethernet cable, and anything connecting will have to go through the wireless. 

I could try plugging in the Mini from someone else's house or work, but that will require me to setup ssh to listen for and forward the proper port, something I haven't yet attempted.

---

### Post by jpkotta on 2008-11-23
Try extra verbosity.  The output from before seems OK.
```
ssh -vvv user@remote
```

---

### Post by employeeno5 on 2008-11-23
Where the below terminates, is where I'm left with the blinking cursor. 

```
broderick@mini:~$ ssh -vv broderick@192.168.0.16
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/broderick/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.16 [192.168.0.16] port 22.
debug1: Connection established.
debug1: identity file /home/broderick/.ssh/identity type -1
debug1: identity file /home/broderick/.ssh/id_rsa type -1
debug1: identity file /home/broderick/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 127/256
debug2: bits set: 506/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.16' is known and matches the RSA host key.
debug1: Found key in /home/broderick/.ssh/known_hosts:1
debug2: bits set: 507/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/broderick/.ssh/identity ((nil))
debug2: key: /home/broderick/.ssh/id_rsa ((nil))
debug2: key: /home/broderick/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/broderick/.ssh/identity
debug1: Trying private key: /home/broderick/.ssh/id_rsa
debug1: Trying private key: /home/broderick/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
broderick@192.168.0.16's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

```

---

### Post by jpkotta on 2008-11-23
I don't know.  The ssh configuration isn't totally fubared because you can log in locally.  Your network is apparently working because you would never get as far as you do if it wasn't.  Your verbose output looks similar to mine.

8.10 client to 6.06 server,
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
```
jpkotta@192.168.0.6's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 131072
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0

```

6.06 client to 8.10 server:
OpenSSH_4.2p1 Debian-7ubuntu3.5, OpenSSL 0.9.8a 11 Oct 2005
```
jpkotta@gauss's password: 
debug2: we sent a password packet, wait for reply
debug1: Enabling compression at level 6.
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152

```

Can you run programs that are not the shell?
```
ssh user@remote ls
```

---

### Post by employeeno5 on 2008-11-26
Hey! Sorry to go missing for a couple days if anyone is still even interested in this thread. I had a few things come up. 

Getting back down to the meat of my troubles:

> Can you run programs that are not the shell?

It would appear that I can't. Doing ls with the ssh still resulted in the familiar cursor of nothing.

I don't know if anyone is still paying attention or has any other ideas, but I'd be happy to try them! :)

Thanks again for all of the help and attention so far.

---

