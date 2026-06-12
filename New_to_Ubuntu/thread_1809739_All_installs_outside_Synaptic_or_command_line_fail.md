---
title: "All installs outside Synaptic or command line failing"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by phubert28 on 2011-07-22
I am running 64 bit 10.10 upgraded from 10.04

After the upgrade the following have not functioned:

Update Manager Install
Computer Janitor
Ubuntu Software Center Installs

Computer Janitor shows packages that need cleanup, but NOTHING seems to perform the cleanup, including Bleachbit.

Does anyone know of any 'setting' in the kernel that could be blocking this?

Computer Janitor stops with the message:

"System clean up could not complete. Be sure no other package manager such as Synaptic or Update manager is running.

None was.

I'd LIKE to FIX the problem rather than reinstall.
Anyone know anyone who might be able to identify this group of symptoms and offer a fix?

They SEEM to have a common source.

I HAVE a fresh 32 bit 10.10 install on another partition but am uncomfortable about moving my current configuration (my data, Firefox and Thunderbird settings, bookmarks, calendars, etc.) over and reinstalling all my apps! It's one bloody lot of work!

My system has gotten progressively slower - boot and shutdown.
[B]
By the way, I'd PAY for local support if it were available![/B]

---

### Post by Paddy Landau on 2011-07-22
As no one has answered this, I will give my suggestion.

I never upgrade the distro; too many problems in my experience.

This is what I suggest:


[LIST]
[*] Ensure that you have backed up your *entire* home directory (including the hidden folders, i.e. those that start with a point such as [FONT=Courier New].config[/FONT]. Exclude [FONT=Courier New].dbus[/FONT]).
[*]Reinstall 10.10 or whatever distro you want.
[*]Restore your entire home directory -- this is where your settings are.
[*]Reinstall any apps you want. Remember that, unlike Windows, when you install (or reinstall) an application, it does not reset your settings. They still exist untouched in your home directory. So, your settings will still be intact.
[/LIST]

---

### Post by phubert28 on 2011-07-22
Thanks, Paddy.

I'm still disappointed that I haven't been able to find anyone who might diagnose the SOURCE of the problem.

Does no one know where to go to find someone who could do that?

I was an RCA/UNIVAC, IBM (MVS-OS/390), Stratus, Tandem, Concurrent (and very briefly Sun) Tech, Assembly language programmer, systems programmer and sysadmin over nearly 40 years.

I wasn't known for timidity. Unfortunately, I've BEEN timid when it comes to my desktop Linux, primarily, I suppose, because I don't like any interruption in service/access. Maybe because I've just gotten OLD! :-(

Now, I have a question: since my /home is on a 64 bit install, CAN it be used on a 32 bit install (which I already have on another partition)????

Too many 'qualifications' when it comes to application updates with 64 bit!

I'm saving your instructions, btw.

---

### Post by oldos2er on 2011-07-22
I don't use Computer Janitor, but if by "packages that need cleanup" you mean to empty the APT cache, you can do that with ```
sudo apt-get clean
```

---

### Post by phubert28 on 2011-07-22
That doesn't affect the list of packages shown in Computer Janitor.

Right now I see a bunch of libreoffice stuff and a couple of google earth items (after executing sudo apt-get clean).

However, it appears SOMETHING I've done has eliminated other packages.
I really DO prefer graphical interfaces to command line.

On Stratus, I created my own 'automated' routines rather than key all that from the command line or try to REMEMBER commands. However, I HAVE no programming skills under UNIX/Linux & either too old or too lazy to try to build them at this point (likely WOULD were I still working and responsible for such environments, but then I'd be PAID to do it and the manual steps would be very annoying to me :-D)

However, do you know if I can use the contents of /home under my 64 bit 10.10 on a 32 bit 10.10 install???

If not, I'll have to do everything from scratch if I want to move to 32 bit.

So, what do you think of 11.04?

I was planning to wait for 12.04 LTS.
Tho, with the Unity interface in Ubuntu, it might be best to think of Kubuntu.

---

### Post by oldos2er on 2011-07-22
Maybe ```
sudo apt-get autoremove
``` is what you're looking, but I'm guessing. apt-get autoremove "is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed."

My opinion is it would be ok to use the same /home/user for 32-bit.

I'm very satisfied with 11.04.

---

### Post by phubert28 on 2011-07-22
Thanks for the suggestion - didn't change anything.

Don't bother further. I have some notes put into Tomboy somewhere and anyway, a fresh install will fix all the problems I've had, anyway.

None of them has been a showstopper.

For some reason, I really loathe touching a working desktop machine right now... gotta get over that, I guess.

If I had the $$$ I'd bypass all the problems under Linux with the proprietary stuff (like MS Office). Most of the Linux techs I know have abandoned the Linux desktop for Apple, some for MS Office, alone (while I know ONE who uses LaTeX and another is an emacs addict!) . Pity. WordPerfect was once such a good competitor and now virtually worthless!

OO and LO have a ways to go. If I ever win a few hundred million, I'll ENDOW them!!!! (:chuckle:)

I'll have to just TRY the /home backup/restore. Haven't even patched the new 10.10 in a few weeks.

I see the new OS X Lion is breaking most of the Adobe products!
Nothing's perfect or perfectly safe.

---

### Post by Paddy Landau on 2011-07-23
> **phubert28 said:**
> However, do you know if I can use the contents of /home under my 64 bit 10.10 on a 32 bit 10.10 install?
Settings are stored on your hard drive, and AFAIK have nothing to do with 32- or 64-bit. So, yes, it's safe to change.

> **phubert28 said:**
> For some reason, I really loathe touching a working desktop machine right now...
That's understandable if you need a reliable system. I'm similar, which is why I stick to the LTS versions. I kept 8.04 until 10.04, and I shan't upgrade until the next LTS comes out.

> **phubert28 said:**
> If I had the $$$ I'd bypass all the problems under Linux with the proprietary stuff
If I'd had the money, I'd have ditched MS and gone Mac -- it's a good system, but expensive. Instead, I ditched MS and went Linux; I couldn't handle all the continuing problems with MS (even though I knew may way around it very well ever since Windows 3.1).

---

### Post by phubert28 on 2011-07-23
As our site downsized and outsourced all our 'big iron', I ended up supporting Windows servers and for awhile the programmers' workstations and their network. I've gotten to dabble in a lot of things since I left my Assembly language programming days on the RCA/UNIVAC, but really expert in none!

I learned about the LTS releases a little late. I had burned a 10.04 before my last Windows croaked the last time I was willing to touch it. With a 2nd HD, I installed Linux and haven't looked back.

I'd already tried OO on Windows, and was using Firefox and Thunderbird, so the transition really wasn't such a problem. If I get my /home backup/restore done and moved over to my clean 10.10 I'm sure I'll be a MUCH happier camper.

After much evangelizing, an older friend finally asked me to install 10.10 on both his PCs and his older Dell runs BEAUTIFULLY on it compared to the sluggish XP (I put 2nd HD's on both systems to guarantee an easy coexistence, as I had with my own Dell, anticipating an eventual move to Linux).

I've been a F/LOSS evangelist since about 1996 - with little effect at work, I'm afraid (state agency).

Thanks again, Paddy, for the reassurance.

I'd favor laws to FORCE -all- public entities (government, education, local boards) to ditch proprietary, tho. We know the IT staff would begin to learn REAL skills instead of the pablum they get in the Microsoft environment! Anyway, it's our tax dollars!!!

I'd LIKE to become more proficient on Linux so I could help more people make the move, but the nearest LUG is in Davis. It's only a little over 20 miles, but a Conservative Republican in DAVIS, CA???? :-D

---

