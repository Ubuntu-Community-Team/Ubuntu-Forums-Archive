---
title: "security: dangerous to do aplay /root/sound.wav ?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-09
Hello,

Regarding security: is it dangerous to do aplay /root/sound.wav ?

Regards

---

### Post by CharlesA on 2010-10-09
You'd have to be more specific.

If it's just a normal sound file, what would it do to harm yer machine?

---

### Post by iponeverything on 2010-10-09
not really. 

If sound.wav was non-root writeable, it might be able to be used as a local escalation.

---

### Post by CharlesA on 2010-10-09
Do you really need to run aplay as root for it to work, tho?

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> Do you really need to run aplay as root for it to work, tho?

I would like to notify with a sound that my script has been completed. script done by root from crontab 

How would you avoid this? but sudo execute needs an users, so again security issues.

Beep is not working on machine

---

### Post by CharlesA on 2010-10-09
Can you just echo something to the screen instead?

I've not used any sounds for scripts that I run. I either have to send me a wall message or shoot me an email to say it's done.

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> Can you just echo something to the screen instead?

I've not used any sounds for scripts that I run. I either have to send me a wall message or shoot me an email to say it's done.

but when you send email, you use mutt / mailx then with root access, ? not good to go on root with some mutt :(

I like to enjoy security in general, apt-get is secured but other root access to net, not particularly good idea.

Sounds, imagine that there is a virus in the wav? (technically it cannot be possible, but who knows)

---

### Post by CharlesA on 2010-10-09
> **honeybear said:**
> but when you send email, you use mutt / mailx then with root access, ? not good to go on root with some mutt :(

The difference is that you aren't running a specific type of file. You are running the mail client.

In either case, if someone got connected and made a symlink to something nasty, you are hosed.

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> The difference is that you aren't running a specific type of file. You are running the mail client.

In either case, if someone got connected and made a symlink to something nasty, you are hosed.

He could use some wireshark thing and uncript some connections to your mail account. I recall that in the past gmail account in mutt was sending pwd uncrypted , like with python gmail notification ...

---

### Post by CharlesA on 2010-10-09
> **honeybear said:**
> He could use some wireshark thing and uncript some connections to your mail account. I recall that in the past gmail account in mutt was sending pwd uncrypted , like with python gmail notification ...

In order to do that, they'd need to get access somehow and if you've secured your stuff properly, they won't be able to get access.

If an attacker somehow got access to the network, you are pwned.

---

### Post by honeybear on 2010-10-09
> **CharlesA said:**
> In order to do that, they'd need to get access somehow and if you've secured your stuff properly, they won't be able to get access.

If an attacker somehow got access to the network, you are pwned.

you mean by sniff ? but you know that routers are easy to go through cuz their password is rarely well set, often as factory, so block ports, change router pwd, and log it heavily

---

### Post by srs5694 on 2010-10-09
A couple of comments/questions:


[list]
[*]Do you need to run the script as root? Many things run from cron do not require root privileges, although some do.
[*]Even if you need to run the script as a whole as root, you can run specific commands as other users by using sudo, as in "sudo -u fred somecommand" to run somecommand as the user fred.
[/list]


Personally, I don't think I'd worry about it for this specific situation. Sure, in principle a bug could be abused to create a system compromise by running bad data through aplay; but the odds of the *specific* file you're using being compromised to affect the *specific* version of aplay you've got seem pretty remote. For added safety, you could just use a sound file that you recorded yourself. That way you know it's safe -- or at least, nobody's intentionally inserted anything nasty into it.

---

### Post by CharlesA on 2010-10-09
> **honeybear said:**
> you mean by sniff ? but you know that routers are easy to go through cuz their password is rarely well set, often as factory, so block ports, change router pwd, and log it heavily

Most routers have remote administration disabled by default and most make it fairly straight forward to secure said router.

I know mine doesn't allow remote administration and since I am using WPA2 with a non-dictionary key, I'm secure from anyone connecting wirelessly. If someone actually broke in and physically hooked up to the router, then they'd have access to any traffic that's on the network.

It's said that physical access = root access, which is true.

---

