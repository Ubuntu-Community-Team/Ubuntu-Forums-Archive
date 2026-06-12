---
title: "Password/Encryption Keys"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-11-02
I noticed that I have passwords in the Password/Encryption Keys program located in accessories. It appears that anybody who walked up to my computer could go look at all my passwords without needing a master password. Did I do something wrong or is this the default behavior? And if so, why? The only reason I noticed was because I downloaded Relevation for a password manager.

---

### Post by 565Customz on 2009-11-02
yeah, its been noticed.

---

### Post by bnhrobotics on 2009-11-03
Do you know any more about it? I assume its not supposed to be that way... Is anything being done about it? Seems like a HUGE security hole.

---

### Post by Ameet on 2010-01-08
> **bnhrobotics said:**
> Do you know any more about it? I assume its not supposed to be that way... Is anything being done about it? Seems like a HUGE security hole.

I just checked it out.  Yes - it looks like a whopper of a security hole.  Any ubuntu experts out there know more about this??

---

### Post by aylons on 2010-01-21
I'm no expert, but...

Anybody that has access to your computer, while you are logged in has access to information you decided to store in your computer.

Well... this lead us to rule #1 of information security: your username and password identify you, and only you. If you don't want people to access your stuff, or behave as you, you cannot let him access any system using your identification. This applies to Ubuntu, your bank account and even your safe deposit or your home.

I mean, this "security hole" sounds like these other, real-life security holes:

[INDENT]
Man, all my documents are at plain sight in my safe! Look, anyone who has access to my safe can pick them up and use the info there to steal my ID!
[/INDENT]

[INDENT]OMG, my car keys are in just sitting in my desk! Anyone who can enter my house may get them and steal my car.
[/INDENT]

If you want to let people use your computer, you should give them a separate login and password, at least a guest one. Any other people using your computer must be supervised or wholly trusted.

---

### Post by tom.swartz07 on 2010-01-21
> **aylons said:**
> I'm no expert, but...

Anybody that has access to your computer, while you are logged in has access to information you decided to store in your computer.

Well... this lead us to rule #1 of information security: your username and password identify you, and only you. If you don't want people to access your stuff, or behave as you, you cannot let him access any system using your identification. This applies to Ubuntu, your bank account and even your safe deposit or your home.

I mean, this "security hole" sounds like these other, real-life security holes:

[INDENT]
Man, all my documents are at plain sight in my safe! Look, anyone who has access to my safe can pick them up and use the info there to steal my ID!
[/INDENT]

[INDENT]OMG, my car keys are in just sitting in my desk! Anyone who can enter my house may get them and steal my car.
[/INDENT]

If you want to let people use your computer, you should give them a separate login and password, at least a guest one. Any other people using your computer must be supervised or wholly trusted.

I agree. 

To easily remedy the situation, just get into the habit of hitting the Lock combination as you get up to leave your computer. Its CTRL + ALT + L, by default, you could change it under keyboard shortcuts if you dont like it.

Thats pretty much the easiest way to assure that no one gets at your stuff, unless they have your password.

---

### Post by _H3MLOCK on 2010-01-21
Well, you logged into the computer, thus proving yourself to the computer (further proof is only needed by commands under the sudo list -- you can remove the passwords/encryption key button using the menu configuration in preferences and/or completely remove it as well. Alternatively you can change the user privilages on the command so it requires sudo access and thus prompting for a password). 
Note: These are only your keys that are saved for use by gpg or ssh protocols.
Locking the computer when you leave it is a good option.
I have my home folder on a crypto_luks filsystem and have a script which unmounts the filesystem on screen timeout. (It needs a password to remount). Plus another script makes sure that f the password is incorrect after 12 consecutive tries then it uploads all data onto a secure cloud (if possible) and writes my home partition with random data. Pretty Cool huh?

---

### Post by rbscairns on 2010-01-21
This "security hole" also surprised me.

I would have expected at least to be asked for my computer login password again, before being able to read in plain text things like my WLAN login password and my email password.

The WLAN login password is the biggie for me. With that, a person outside of the office can relatively easily access the office NAS with just thier WLAN enabled laptop. Even my staff (all using XP) don't know this password.

---

### Post by aylons on 2010-01-21
If a password was needed to access your passwords... there would be no need of having a password manager. Actually, you should get rid of it.

Because, whenever a password is to be accessed by the system, either it does have to decrypt it (using a key, ie, a password) or it is already readily accessible. Any other option will just deceive the user with a false sense of security. 

That's because anyone with basic knowledge of computers would be able to google and find a password viewer in no time, specially for a well know system as Ubuntu is. And the user would still feel safe about their passwords.

If you have any doubts, I can show how this has already happened with an app that, arguably, os way less targeted than Ubuntu: Google for "Opera Wand" and for "opera password recovery".

In short, Opera Wand implements just what you want: an obfuscation algorithm so the passwords stored are not easily read, yet the system could still use them automatically. However, there are lots of apps, easily found on google, that retrieves all passwords stored in no time (I mean, really just as fast as opening a text file).

I don't know if someone actually did it, but I can figure how to make an web app that would make this password recovery as simple as accessing a web page and uploading a file.

Futher info about this specific case may be found in Opera Forums.

**********

Actually, I have a better example for how dangerous would be if Ubuntu behaved otherwise. It's plain shown in the post before this:

> The WLAN login password is the biggie for me. With that, a person outside of the office can relatively easily access the office NAS with just thier WLAN enabled laptop. Even my staff (all using XP) don't know this password.

Let me tell rbscairns something: chances are your staff already know this password. Probably they needed it sometime for changing configuration or for not having to ask you for typing it whenever they make a mistake with Windows XP settings. They just don't tell you that.

If you have any doubt, test for yourself: google for "Wifi password recovery" and you will find software that just do that: recover passwords stored in the machine for WEP, WPA and WPA2. 

Even if your staff is completely trustworthy (I don't doubt that), they may be not fully aware of the danger of this situation. Then, someone could easily gain access for a couple of minutes (or even seconds if he is prepared) and get your password as easily as you can read this post now (or even more, as for reading this post you must be connected to the internet).

Actually, I really thanks Microsoft for this deceiving approach. My girlfriend's college only provides wifi to student's laptops, and each student can only have two laptops. No cell phones, PDAs, or boyfriend's computers.

However, as I know that there is no way of truly hiding information without a key, I googled  for a solution and in five minutes her Treo Pro and my computer were online, thanks to WirelessKeyViewer.

[http://www.nirsoft.net/utils/wireless_key.html](http://www.nirsoft.net/utils/wireless_key.html)

As a bonus, this website also can show you other applications with the same problem.

---

### Post by aylons on 2010-01-21
The Nirsoft website has a nice list of software that insecurely stores passwords and where to find them. Some of them are completely justified - how nasty would be if an email program asked you for password every time it checked for new mail?

So, how does Ubuntu security differs from Windows when it comes to password management?

First of all, Ubuntu provides a centralized system apps can use, while Windows apps are pretty much on their own. Some people may say it is a security hole, as it would make it easy for an intruder to inspect every password at once.

But it isn't.

This centralized management means that passwords can be kept safe without the need for the user typing a master password each time an application wants to retrieve them: when you insert a password (eg, a WPA2 key) in a application (it would be the Network Manager), the app handles it directly to the password manager (keyring for short). When it wants to use the password (for logging into a network), it asks the keyring which delivers it.

The secret is that inside keyring, the data is encrypted and only the user can decrypt it. I mean, really, ONLY the someone who knows the password can access it - not even root will be able to retrieve the data. Not even if someone steals your computer and spends years trying he will be able to open the file.*

And, as the master key for keyring is your user password**, you get all this security in a transparent package: type your password for logging in, don't need to type any other password.

=======

*Assuming that you have choose a strong password for your user account and that knowledge of encryption will not change drastically in the next years.

** Even though the password for the user and for the keyring are usually the same, simply retrieving the password hash file in the linux system won't be enough for decrypting the keyring files. But surely it would help.

***I've created another post because I really want the one above to out stand. I mean, it's a live proof of my argument: obfuscation is the security hole, and plain show is just good user education.

---

### Post by bigbaraboom on 2010-07-28
'Password and Encryption Keys' used to prompt for your login key back in Jaunty (9.04)! 

If entering your password when logging into Ubuntu is so incredibly safe... as to allow anyone to see your keys in plain text with a single click,
then by the same logic why do we need authentication for Synaptic, Software Sources etc.? Why do we need root privileges at all? 

What is wrong with a keyring manager prompting users to authenticate before letting them see a hundred valuable passwords :rolleyes:

---

### Post by mcduck on 2010-07-28
> **bigbaraboom said:**
> 'Password and Encryption Keys' used to prompt for your login key back in Jaunty (9.10)! 

If entering your password when logging into Ubuntu is so incredibly safe... as to allow anyone to see your keys in plain text with a single click,
then by the same logic why do we need authentication for Synaptic, Software Sources etc.? Why do we need root privileges at all? 

What is wrong with a keyring manager prompting users to authenticate before letting them see a hundred valuable passwords :rolleyes:

Root is a different user, and security between user accounts is something that affects your overall security on a machine with a network connections. In addition it serves as a restriction between different user accounts, giving one of them ability to administer the system while allowing others to have less privileges (remember, even if you are the only one using your computer, it's still a multi-user operating system).

On the other hand accessing the passwords and encryption keys as your own user is something that would only be a local vulnerability (if it would even count as such, since your security is already completely gone at the second you let somebody have unrestricted access to your machine locally. Physical access=full access, no matter what you try to do about it. Having the password manager request a verification would make no difference since by leaving the desktop unlocked you have already compromised not only your passwords, but all your files and the account itself. Even if the computer is locked/shut down physical access allows accessing all the data in it, by booting to a live OS (no, you can't actually stop that with any BIOS setting as such settings are easy to reset) or by removing the hard drive and reading it on another system.

So it's really simple: If you don't lock your session when you leave the computer unattended, you have compromised your user account and it's files. If you leave anybody with unrestricted physical access to the machine, you have compromised the whole system and everything in it. In the case of the Seahorse app not being locked you have already done one of these things so it makes no difference. Having such a password confirmation would only giver you a false illusion of security, while you actually should just learn to lock the desktop (which would protect not only your passwords, but also your files and the account itself, at least to the point that anything can be protected if somebody has physical access).

edit: and no, Seahorse has never prompted you for a password once you have already unlocked the keyring. If you were prompted for it in 9.10 you must have been using an automatic login (not a thing for anybody concerned about security, by the way) or  had different passwords for your account and keyring so that the keyring didn't get unlocked at login time like it should.

---

### Post by bigbaraboom on 2010-07-28
@mcduck

Thanks for sharing your thoughts and understanding on the topic. I did a search last night, and it appears to be debated on a large scale.

Having said that I understand some of the logic behind your explanation, but I'm not too convinced this is a particularly good way to handle sensitive information. For example, why do we need to see the passwords at all? I'm not too worried about anyone gaining physical access to my system (unless I get robbed [-o<), but more of the idea that the keyring manager would hand out keys to any program that happens to make a request for them, and because of how we unlock the manager (login password). It's like 'putting all of your eggs in one basket'.

I won't go any further as I am not qualified to convincingly defend either side of an argument, but I do know that 9.04 (not 9.10..typo) had an authentication prompt before revealing passwords in plain text.

---

### Post by CzarDerivative on 2010-09-08
Quick fix:

The following will ghost out the "Show Password" button so that it cannot be activated. Note that this is not a security fix... but it will prevent the average "dumb" user from being able to see all of your passwords after you lent them a browser and went to the bathroom. 


edit /usr/share/seahorse/ui/seahorse-gkr-item-properties.xml

Search for:

```
<object class="GtkCheckButton" id="show-password-check">
...
</object>
```

and add the following:
```
<!-- Desensitize the Show Password checkbutton to prevent casual users from seeing my passwords -->
<property name="sensitive">False</property>
```


-Oren

---

### Post by jorgealfonso on 2011-05-08
Thanks CzarDerivative! that made it at least for my most urgent need: keep my passwords safe from an average, not linux savvy, person using my computer

---

### Post by White-Energy on 2011-06-11
I've just noticed this.. and its very dangerous.. i can lose everything i have if anyone can see my password, anyway, after i've seen CzarDerivative's post i thought i should play with it and hide all the Password dialog.. so i found how to diffidently hide it so no one can change or see.

Here's what i did.
First you'll need to open the file with

```
sudo gedit /usr/share/seahorse/ui/seahorse-gkr-item-properties.xml
```

and search for this line

```
<property name="visible">**True**</property>
```

and change it to this (or just change the True to False instead of copying)

```
<property name="visible">**False**</property>
```

And you're good to go! :D

---

