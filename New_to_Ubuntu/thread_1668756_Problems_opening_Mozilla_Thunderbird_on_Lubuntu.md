---
title: "Problems opening Mozilla Thunderbird on Lubuntu"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by watergipsy on 2011-01-16
Hi,

I've just switched to Lubuntu and am pulling my hair out at the challenges of getting things up and running for working with it. Considered myself a competent Windows user... The switch was the solution suggested after two virus attacks in a fortnight and very slow operating speed. I am within a hair's breadth of getting a new laptop, probably with Windows if I'm honest, which I really don't want to do as this one is functional, if old and a bit clunky, and in any case I don't like to be beaten.

Current challenge, which is high priority to resolve so I can do my paid work on this machine, is as follows:

I'm trying to tranfer all my work emails from Outlook Express on Windows to Mozilla Thunderbird on Lubuntu.

I've copied emails and addresses across (via Thunderbird on Windows) and have gone through the process for getting the copied profile to be the default profile. But... when I tried to open Thunderbird after completing this process, I got an error message:
"Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system."
I had opened and closed it several times without any problems before this happened.

Since the error message first appeared, I have rebooted my system several times. I tried using LXTerminal to kill any processes which seemed to related to Thunderbird. I have shut my laptop down a left it for a week. Still the problem persists. And I can't find any helpful information about how to solve this problem.

I have been advised to set my system so that it doesn't save processes from one session to the next to prevent this, but can't find how to do this either, but would love to know.

I have just tried 
sudo pkill -u user
as suggested by Future Pilot on
[http://ubuntuforums.org/showthread.php?t=1533916&highlight=kill+processes](http://ubuntuforums.org/showthread.php?t=1533916&highlight=kill+processes)
(Sorry if this is the wrong way to reference a previous post.)

I think the computer guys put me on Lubuntu 10.10 in the end (it was the only one which would work with my mobile broadband dongle) but I'm not even sure about that and can't find where it tells me if this is the case, so if you need this information to offer advice, please could you tell me where to find which version I'm on!...

Look forward to someone saving my head of hair!
Thanks. And apologies for not using the best way for referencing, quoting etc - I'm totally new to forums... Hope my post is still easy enough to follow.

---

### Post by davidmohammed on 2011-01-16
[this]("http://kb.mozillazine.org/Profile_in_use") should be interesting info for your issue.  You probably have a lock file that doesnt get cleared on reboot.

You mentioned you "copied" your windows profile to linux.  I dont think that will work because various config files have hard-coded and relative paths in them that will be different in ubuntu.  Suggest use a brand new profile.

---

### Post by watergipsy on 2011-01-16
Wow! Thank you! That was easy - I undid the process I used to get the new profile used in place of the old one, and it now opens! But then I'm still stuck because I've now re-followed the instructions I found on Howtoforge.com ([http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution_p2](http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution_p2)) for copying the profile and again the error message appears and Thunderbird won't open.

I have an email address book of some 300 people and archived emails from the history of the project I work for so a brand new profile isn't an appropriate option - I really need to copy the stuff that's currently in Outlook Express.

This is what I've done which is as close as I can get to the howtoforge instructions:
- copied the profile folder 2iozx6xz into home/user (wouldn't allow copy into home directory)

- opened a terminal and copied the profile directory to the .thunderbird directory (slightly different directory name for thunderbird on howtoforge, but this is definitely what mine is called):

Code:
cd ~
mv 2iozx6xz.default/ .thunderbird/

- backed up new profile file:

Code:
cp ~/.thunderbird/profiles.ini ~/.thunderbird/profiles.ini_bak

- instructed use of new profile:

Code:
gedit ~/.thunderbird/profiles.ini

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
# Path= vufmnitg.default
Path= 2iozx6xz.default

- restarted Thunderbird and got the error message again...

I should add that when I copied the profile from Outlook Express into Thunderbird on Windows, all the emails and addresses were there, no problems.

---

### Post by SteveDee on 2011-01-17
You may have a permissions problem with files & folders that you have copied. You need to be the owner (with read/write permissions) for your /home/{name}/.thunderbird/ folder and the profile folder.

Also look at this: [http://kb.mozillazine.org/Moving_from_Windows_to_Linux](http://kb.mozillazine.org/Moving_from_Windows_to_Linux)

---

### Post by watergipsy on 2011-01-17
Thanks for your suggestions. I've checked that my login has administrator rights - in fact it's the only one on the system.

I've also had a look at the link you suggested and tried the actions recommended if Thunderbird won't start:

Quote:
If the application doesn't start, type locate run-mozilla.sh in a terminal. It should return the directories that have that file, which also contain either the "firefox" or "thunderbird" shell scripts used to start the application. Type echo $PATH into a terminal and verify the directory is on the path.

locate run-mozilla.sh returned:
usr/lib/firefox-3.6.13/run-mozilla.sh
usr/lib/thunderbird-3.1.7/run-mozilla.sh
usr/lib/xulrunner-1.9.2.13/run-mozilla.sh

echo $PATH returned:
usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

This is all gobble-de-gook to me, but I assume that as there is nothing named thunderbird in the second set of information that this is where the problem might lie...? The mozillaine doesn't seem to tell me what to do next. Any further suggestions gratefully received.

---

### Post by SteveDee on 2011-01-17
> **watergipsy said:**
> Thanks for your suggestions. I've checked that my login has administrator rights - in fact it's the only one on the system.

Just so there is no misunderstanding, if your username is "watergipsy" then when you go to the /home/watergipsy/.thunderbird folder (in file manager) and view Permissions, the owner should be: watergipsy and owner access control should be: Read and write. The same should apply for /home/watergipsy/.thunderbird/profiles.ini and the profiles folder. If the owner is "root" you have a problem.

If this looks ok but you still have a problem, I suggest you try again & note the following:-
 - On your Windows version of Thunderbird, try to uninstall any addons (this has caused me compatability problems in the past).
 - Once you have copied your profile to the .thunderbird folder, run the profile manager from a terminal like this:-
```

thunderbird - P

```
...give your profile a name (say "watergipsy") and then browse to your profile folder.

Once this is done, open Thunderbird. You should be able to access your mail and address book.

---

### Post by Rowanmf on 2011-01-17
i dont have an exact solve for you but i think you need to know there are many ways to skin a cat - 
I used to have a dual boot system at work ubuntu and xp , XP was what i started with and added Ubuntu later , so all my emails were in outlook . 
After much searching and fiddling i loaded thunderbird on both XP and ubuntu , then i left a fat partition inbetween the two for files that both of them needed . I then imported all my emails from outlook into thunderbird and then moved the whole profile to the fat partition along with my docs .
then when i was in ubuntu i pointed the thunderbird to the fat partition for its profile .
Hey presto all my emails were there and it did not matter which OS i collected them in they would always be there .. i used that system right up until 10.4 .
I hope this gives you another angle of attack .

Cheers

---

### Post by watergipsy on 2011-01-18
Thank you SteveDee and Rowanmf for your suggestions. Bizarrely, totally bizarrely in fact, I took the default profile back to the original one and then reapplied the copied one as the default as I had done already, and now Thunderbird opens with all my copied emails there... I have absolutely no idea why that happened and why it wouldn't do so before. I'm not aware of having changed **anything** in checking the file permissions which were all fine anyway!

Anyway, the key is I have achieved what I was trying to, and I only hope I achieve the same when I try to upload the latest version of my profile.

Thank you so much for your time in trying the resolve the problem. :)

---

### Post by watergipsy on 2011-01-18
And now I've uploaded the most up-to-date profile from Outlook, no problems, and even downloaded emails, no problems! Totally inexplicable change! 

Thanks again for the responses and suggestions!

---

