---
title: "&quot; ? &quot; beside application, and other puzzles"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Rich in Amsterdam on 2009-11-13
[COLOR=Black]What does it mean if the image beside an application is a small white page with a [COLOR=Magenta]? [COLOR=Black]on it? Does it mean the application is not properly installed? (e.g. Amarok)

I am an utter idiotic newbie. Had Kubuntu (version of at least 18 months ago) sitting dormant on the extra hard disk (Win2000Pro on the other) on my old Compaq W6000. Plucked up the courage to get started, and immediately updated to Karmic. I like it very much, am already up and running for my mail and internet, but there are one or two problems.

Are they real problems, or just results of my complete ignorance?

Mozilla Thunderbird:  Help won't open at all. Neither will Release notes.
Bug report and About will open.

On the Welcome page, the link to Thunderbird Help Centre does nothing.

Amarok doesn't want to do anything most of the time. It sometimes opens and then disappears again in a second or so. My sound files won't (first they didn't, then they did for an hour, now they won't)  play in Amarok, but will play in Dragon Player. Sound off the internet is fine. 

Adept:  The handbook refuses to appear. I get: 
    "The file or folder help:/adept/index.html does not exist."
I don't understand Adept. Need the handbook. It produces a nice long list, then wipes it off before I can read it all, and tells me I can go back to installing or whatever!

Bash works allright, but the Run Command button on the Computer tab of the launcher produces a little GUI-style terminal which won't do nuffin!

The help centre talks about Kcontrol and Control Centre Modules. Can't find 'em.

I'm not expecting detailed solutions for everything - I'm just mentioning a number of things to give an impression, as it were, so you can perhaps tell me, for example:
[/COLOR][/COLOR][/COLOR][COLOR=Black][COLOR=Magenta][COLOR=Black]Did I mess up the Karmic installation? Are there things I need to 'activate', as it were?[/COLOR][/COLOR][/COLOR]

I WILL be staying with Linux. All help very much appreciated.

Richard
[COLOR=Black][COLOR=Magenta][COLOR=Black]

[/COLOR][/COLOR][/COLOR]

---

### Post by ohzopants on 2009-11-16
A lot of things have changed since the version from 18 months ago; that's 3 whole release cycles.

For instance, amarok 1.x has been replaced by 2.x and KDE 3.x has been replaced with 4.x so a lot of the "stock" kde apps have likely undergone major change.

The issues you're having are probably due to your upgrade trying to update packages which simply aren't maintained anymore.

In your situation, I would likely start over with a fresh install.  If you have a separate partition for you data (which you are more likely to have if you were dual booting) this shouldn't take  more than about an hour or two.

---

### Post by mrboojive on 2009-11-16
I agree. At the very least, the ? icon means that the icon for that application is not installed. And that suggests to me that the application itself is not installed properly. With all these strange issues, it sounds like you should just do a fresh install.

> **Rich in Amsterdam said:**
> Bash works allright, but the Run Command button on the Computer tab of the launcher produces a little GUI-style terminal which won't do nuffin!

Are you just typing terminal commands into the "Run Command" box? It is probably doing stuff, but not showing you the output. I find that it is a lot more useful for launching applications than running terminal command. Press Alt+F2 to bring it up, then start typing the name of the application, e.g. "Firefox" and then press enter. Here is a list of a lot of cool things you can do with that box: [http://userbase.kde.org/Tutorials/Krunner](http://userbase.kde.org/Tutorials/Krunner)

> **Rich in Amsterdam said:**
> The help centre talks about Kcontrol and Control Centre Modules. Can't find 'em.

Those are probably referring to the "System Settings" program. Click on the K Menu, go to Computer, and click on "System Settings."

---

