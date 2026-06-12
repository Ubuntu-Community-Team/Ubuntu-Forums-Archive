---
title: "Moving mail from Mozilla in Vista to Ubuntu"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Jos.vh on 2011-04-14
Hi.
I'm a new Ubuntu user and I've installed Ubuntu on my laptop (dual boot). Thanks to previous posted questions and answers, this operation was a great success! Thanks to everyone who contributes to this forum!
Because of the success on my laptop, I'm now planning to re-install my desktop pc, which currently runs Windows Vista. 
To do this, I bought a bigger hard disk and I'm not planning a dual boot (wouldn't be easy, even if I wanted to, because the pc was bought with Vista pre-installed and no Vista cd included). (pc is a Packard Bell- very small case- with no space for a second hard disk:()
On the current pc I run Mozilla for windows (3.0) and there is a lot of mail that I would like to keep (backup) and then restore in Ubuntu. 
I tried MozBackup, to backup Mozilla and considered moving these files to the laptop (were there is a Windows XP dual boot installed) so I would at least be able to read the mail if necessary, but that didn't work (the generated file was much to small to contain all the mail, because the total size on disk is about 900 Mb - yes I know....time to clean-up my mail.....;)). 
So here is my question:
Is it possible to backup/move my mails and address book to Ubuntu (Mozilla or Evolution) ? And how do I fix that?

Thanks in advance.
Jos

---

### Post by josephmills on 2011-04-14
it might be possible who is your mail carrier?

---

### Post by wolfen69 on 2011-04-14
Are you using Thunderbird?

---

### Post by Jos.vh on 2011-04-15
> **wolfen69 said:**
> Are you using Thunderbird?
Yes, I'm using Thunderbird.

@josephmills: mailcarrier? I don't now what that means but I'll let you now if I found out.

---

### Post by amoeba801 on 2011-04-15
It’s fairly easy to move a Thunderbird account from one machine to another, and from one OS to another. I’m doing it all the time with my wife’s email; now up to 2.4G of email going back 10 years. All moved safely, time after time.

Detailed information on how to do this can be found on the Mozilla website, but my approach is as follows (moving from Vista to Ubuntu):

[LIST=1]
[*]On Vista, shut down Thunderbird
[*]Copy the Thunderbird profile folder and all its contents onto a USB stick or similar. The profile can be found somewhere like:
[FONT="Courier New"]C:\Users\xxxx\Application Data\Thunderbird\Profiles\y4zu0xk5.default\[/FONT]
where [FONT="Courier New"]xxxx[/FONT] is your vista username

[*]On Ubuntu, shut down Thunderbird
[*]Copy the folder and its contents on the USB stick into the Thunderbird folder in your user account, which can be found here:
		[FONT="Courier New"]/home/xxxx/.thunderbird/[/FONT]

where [FONT="Courier New"]xxxx[/FONT] is your ubuntu username

so you end up with a profile folder like

[FONT="Courier New"]/home/xxxx/.thunderbird/y4zu0xk5.default/[/FONT]

[*]Finally edit [FONT="Courier New"]/home/xxxx/.thunderbird/profiles.ini[/FONT] to point to this profile. It should look similar to:
[/LIST]

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=y4zu0xk5.default

```

This method assumes you want to use the profile from Vista, but the same approach can be used to move from one Ubuntu machine to another.

This also assumes you want to use the profile as is, replacing any existing rather than merging an old profile into a new profile.

---

### Post by David_UK on 2011-04-15
> **Jos.vh said:**
> Is it possible to backup/move my mails and address book to Ubuntu (Mozilla or Evolution) ? And how do I fix that?
No problem.  It's pretty easy to copy your whole profile from Windows and pop it into Ubuntu.  Make sure you are using the same generation of Thunderbird to ensure compatibility.
Look [here]("http://kb.mozillazine.org/Moving_your_profile_folder") for mozilla's own instructions, plus there are a few other guides if you seach for 'move thunderbird profile' or similar.

Post back if you have trouble.

Incidentally, you don't need the vista disk to dual boot with ubuntu - you can add it alongside on the same disk.

Also, if you get very keen, it's possible to access you thunderbird mail from both windows and ubuntu on your dual boot pc.  I recently learned how - click [here]("http://ubuntuforums.org/showthread.php?t=1701190") if you want to.

Edit: Sry amoeba801, didn't see your post before I posted.

A final thought - as I recall, you need to make sure you create a new, dummy profile with your new thunderbird installation before you can paste your old profile into the folder.  Otherwise the folder structure isn't there.

---

### Post by Jos.vh on 2011-04-15
Thank you very much for the advice!!!! Now I have something to try this weekend. I'll let you know the result.
Have a nice weekend!

Jos

Edit: It is solved!!! Works perfect! Now my desktop pc has got a new Hard disk and is about to become a Ubuntu-only pc in a few moments. (You might see some new questions later today......)

---

