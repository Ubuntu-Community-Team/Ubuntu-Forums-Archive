---
title: "Empathy Can't Identify: Unsupported command /msg"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-16
When I put in my password and stuff into empathy, I thought it would auto-ident for me, but it didn't, and I cannot use the /msg command!

---

### Post by Dougie187 on 2009-11-16
What protocol are you using?

---

### Post by coldReactive on 2009-11-16
> **Dougie187 said:**
> What protocol are you using?

Uhh, IRC, freenode?

---

### Post by Dougie187 on 2009-11-16
Hmm. That's weird. It works for me. Can you do it in pidgin?

Well, not the /msg, but the auto-ident works.

---

### Post by coldReactive on 2009-11-16
> **Dougie187 said:**
> Hmm. That's weird. It works for me. Can you do it in pidgin?

Well, not the /msg, but the auto-ident works.

Yes, I can do it in pidgin. NickServ doesn't even give an error stating that the password is wrong, so the auto-ident didn't even go through.

There is no checkbox anywhere to see if it auto-idents in the first place on the edit account thing, so I'd think it's automatic.

---

### Post by Dougie187 on 2009-11-16
Yeah, for me after I enter my information a little notification comes up that tells me it identified for me. Though it wasn't instant, it took a little while, but no more than about 30 seconds.

---

### Post by coldReactive on 2009-11-16
> **Dougie187 said:**
> Yeah, for me after I enter my information a little notification comes up that tells me it identified for me. Though it wasn't instant, it took a little while, but no more than about 30 seconds.

Yeah, that... didn't happen.

---

### Post by Dougie187 on 2009-11-16
I could see how this is an issue though. At least, if it doesn't work.

I would assume you have tried removing the account and reentering your information multiple times?

I stopped using empathy because I couldn't change tabs with ctrl+tab.

---

### Post by coldReactive on 2009-11-16
> **Dougie187 said:**
> I could see how this is an issue though. At least, if it doesn't work.

I would assume you have tried removing the account and reentering your information multiple times?

I stopped using empathy because I couldn't change tabs with ctrl+tab.

Well, I put it in again, and finally it identified.

---

### Post by Dougie187 on 2009-11-16
Thats good. Maybe you just had some of the information in wrong or something.

---

### Post by coldReactive on 2009-11-16
> **Dougie187 said:**
> Thats good. Maybe you just had some of the information in wrong or something.

Well, I think it's because I used a lowercase r instead of an uppercase one in my nick.

---

### Post by computer_freak_8 on 2010-01-20
Sorry if I shouldn't dig up this grave, but this same issue was driving my bonkers; I didn't want to unnecessarily spew duplicate threads, but I did want to get this out there in hopes that someone else will benefit.

This is something I just discovered by accident, after having the same issue myself. Here's how I got mine to work:

My system is updated (don't know if this matters or not, but it can't hurt)

Where you would normally type: ```
/msg NickServ commandname
```Instead, connect to the NickServ "user" (don't know if that's the proper term) and just type: ```
commandname
```

For example:
(Key: **bold is what I type**; *italics is the Empathy built-in response*; normal is the server's response.)
```
**/msg NickServ help**
* - Unsupported command*
**/msg nickserv help**
* - Unsupported command*
**help**
NickServ: ***** NickServ Help *****
NickServ: NickServ allows users to 'register' a nickname, and stop
NickServ: others from using that nick. NickServ allows the owner of a
NickServ: nickname to disconnect a user from the network that is using
NickServ: their nickname.
NickServ:  
NickServ: For more information on a command, type:
NickServ: /msg NickServ help <command>
NickServ: For a verbose listing of all commands, type:
NickServ: /msg NickServ help commands
NickServ:  
NickServ: The following commands are available:
NickServ: GHOST           Reclaims use of a nickname.
NickServ: GROUP           Adds a nickname to your account.
NickServ: UNGROUP         Removes a nickname from your account.
NickServ: IDENTIFY        Identifies to services for a nickname.
NickServ: INFO            Displays information on registrations.
NickServ: LISTCHANS       Lists channels that you have access to.
NickServ: REGISTER        Registers a nickname.
NickServ: SET             Sets various control flags.
NickServ: RELEASE         Releases a services enforcer.
NickServ:  
NickServ: Other commands: ACCESS, DROP, HELP, ID, LISTOWNMAIL, LOGOUT, 
NickServ:                 MYACCESS, SETPASS, ACC, STATUS, TAXONOMY, 
NickServ:                 VACATION, VERIFY
NickServ: ***** End of Help *****
```


Also, I discovered I really like XChat better for IRC anyways, but it is nice to know that now I can use Empathy for IRC (without much hassle), too.

---

