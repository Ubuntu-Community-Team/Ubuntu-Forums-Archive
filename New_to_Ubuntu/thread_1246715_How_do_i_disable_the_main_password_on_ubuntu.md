---
title: "How do i disable the main password on ubuntu"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Windows_suckz on 2009-08-22
How do i disable my password on Ubuntu 9.04 it bug's me every time i do something, it pops up and asks for my password any help would be appreciated :confused:

---

### Post by lisati on 2009-08-22
For the login screen you might want to look into automatic login. For other situations I'd advise against it for security reasons.

---

### Post by earthpigg on 2009-08-22
> **lisati said:**
> for the login screen you might want to look into automatic login. For other situations i'd advise against it for security reasons.

this.

in fact, ubuntuforums.org policy prohibits us from telling you how to _*enable the root account in ubuntu*_, but you are welcome to google it if you would like to ignore our advice.

---

### Post by Codix121 on 2009-08-22
Yes it is infact possible to enable it,
but it defeats the whole purpose of "linux" security,
I mean sure it's annoying but it's a lot safer and stable.
The reason we do "sudo" is precisely for safety,
Disabling could leave you at serious risk,
but feel free to look, I just personally wouldn't
recommend it.

---

### Post by 3rdalbum on 2009-08-22
> **Windows_suckz said:**
> How do i disable my password on Ubuntu 9.04 it bug's me every time i do something, it pops up and asks for my password any help would be appreciated :confused:

It's not "every time I do anything". Ubuntu asks for your password in order to elevate your privileges to root. The only time it asks is if the program you're trying to run requires root privileges. It can't elevate the program without authenticating.

It's one of the differences between Linux and Windows (XP). If you can't handle this difference in respect for the Linux security system, then it's possible that Linux is not for you. And as Windows Vista and Windows 7, and Mac OS X are moving in this direction too, maybe you should just get used to it.

There are lots more differences!

Good luck,

Chris.

---

### Post by dk06 on 2009-08-22
> **earthpigg said:**
> this.

in fact, ubuntuforums.org policy prohibits us from telling you how to _*enable the root account in ubuntu*_, but you are welcome to google it if you would like to ignore our advice.
Wow, I had no idea that it was against policy to do that..???

__________________________________________
?

[LIST=1]**When answering technical support issues:**
[*]Be considerate to the person asking the question. We were all a green user at one point. Yes, some users are harder to help than others, but please be respectful to all users.
[*]Try to avoid acronyms and jargon when giving instructions. New, or "green" users may not be able to follow you, and many will not ask you for an explanation in order to avoid looking stupid. RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.
[*]If the users' question has been covered in one of the community documents, please give them a description and the links. Some useful sites to point green users are: wiki.ubuntu.com, [www.ubuntu.com](www.ubuntu.com), and the forum HOWTOs. You can also show the user how to search the forums or tell them about the forum search utility. If you wish to remind a user to use search tools or other resources when they have asked a question you feel is basic or common, please be very polite. Any replies for help that contain language disrespectful towards the user asking the question, i.e. "STFU" or "RTFM" are unacceptable and will not be tolerated.
[*]Always assume the the user has a default installation unless you're told otherwise. If you tell people to use an application outside of the official Ubuntu installation, please give instructions on how to install it.
[*]Always assume that the user is a new user unless you're certain the user is not. Please remember to give detailed instructions as some users do not know how to get to a terminal yet.
[*]To avoid confusion and auto-formatting issues, please use [CODE] tags around terminal commands. If an image speaks a thousand words and can show exactly what you mean, by all means, include an image.
[*]Please wrap long outputs from commands or other text to prevent users from needing to scroll through the content inside [CODE] tags.
[*]Please remember to do things the Ubuntu way. There are always more than one solution to a problem, choose the one you think will be the easiest for the user. Automatic package installation (using Synaptic, Aptitude, or apt) over manual installation. DEB over source. Please never instruct users to do anything that might break their system, this includes using --force and -ignore-depends when installing a DEB. Try to think as a green user and choose the simplest solution.
[*]Explain each step of the solution. If possible, try to teach the user while giving a solution to them. Teaching begets more teaching. :)
[*]If you're uncertain if a procedure is correct, please tell users so. If your procedure has inherent risks, please tell users what they are. For example, if you're teaching someone how to resize a partition, please include a disclaimer that it MAY occasionally cause data loss. Also, please make sure all information and assistance you give is accurate to the best of your knowledge, will give the intended outcome, and is not based on guesswork.
[*]Replies to questions that ask for help running legitimate software (albeit closed source or proprietary) that do not answer the question, but instead instruct the user that they should not be using that software on the grounds that it is not free serve only to frustrate and confuse the user and will be removed to make room for answers to the question the user asked at the moderator's discretion. The goal of this forum is to first provide technical assistance and then to educate users on the benefits of free software.
[/LIST]

---

### Post by 3rdalbum on 2009-08-22
> **dk06 said:**
> Wow, I had no idea that it was against policy to do that...is sudo bash okay?

...technically it's not root

Advising on how to get around Ubuntu's security configuration is prohibited. The commands "sudo bash" and "sudo -i" are okay, as they work within the Ubuntu security system.

---

### Post by CatKiller on 2009-08-22
> **dk06 said:**
> is sudo bash okay?

I understand that ```
sudo -i
```is the recommended method.

---

### Post by ibuclaw on 2009-08-22
> **dk06 said:**
> Wow, I had no idea that it was against policy to do that..???

There is a sticky in the "[Security Discussions]("http://ubuntuforums.org/showthread.php?t=716201")" subforum of the Main Support Channel.

As for configuring sudo, you can allow all programs to run without password access. But I vouch against that type of security paradigm.

For configuring sudo for your needs, [I've written a guide here.]("http://ubuntuforums.org/showthread.php?t=1132821")
That should answer any questions you have.

Regards
Iain

---

