---
title: "Apps will not install"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by averyfriendlylion on 2010-05-02
I have recently installed Ubuntu 9.10 off a Linux Beginners Kit CD free with Linux Format magazine. I am an absolute beginner, in the purest sense, and I already feel distinctly out of my depth. However, having wired up a chunk of my budget hard-drive to accommodate Ubuntu and with a dogged determination to make sense of it (mainly driven by the distros virus-like refusal to be removed) I have ended up here. My first question probably sounds completely retarded.

The question is, why, when I go on Ubuntu Software Centre and I click on an application (namely Exaile) under 'Get Free Software', can I not install it? When I arrive on the Exaile application, I see the message 'Not available in the current data' and the 'File' drop down menu does not allow me to install. What does this mean and how can I solve this problem?

ALSO - I cannot play MP3 files on Rhythmbox. Am I going to solve the problem by installing Exaile? If not, what can I do?

---

### Post by averyfriendlylion on 2010-05-02
ALSO - I have downloaded a number of Tar files ('tar.bz2''tar.gz') which I cannot 'Install' i.e. turn into working applications. These include the Midori and Kazehakase web browsers. When I open them currently I simply arrive at reams of files filled with code. 

I understand I have to enter some sort of code into a 'terminal'. After searching I was only able to locate the 'gnome terminal'. Having clicked the file a text box appeared saying there was 'no installed viewer capable of displaying the document. Have I made an error so far? What can I do to run these Tar files?

---

### Post by snowpine on 2010-05-02
Welcome to the forums! I know Linux can be a lot to learn, try not to get overwhelmed. :)

I have not personally used the Software Center (I am a terminal guy) but does it have a Refresh button? There should be someplace you can click to reload the list of available applications from the Ubuntu server. If you can't figure out how to do it, you can type this into the Gnome terminal:

```
sudo apt-get update
```

I am fairly optimistic that once you refresh this data, you should be able to install Exaile. 

You can install the package "ubuntu-restricted-extras" from the Software Center to get a whole bunch of yummy multimedia codecs, including mp3 and Flash video support.

You should also use the Software Center to install Kazehakase and Midori. This is the recommended method, not downloading stuff from the Internet like you might be used to from Windows. Ubuntu uses a central trusted "repository" of applications (accessed through the Software Center) which is one of the main reasons it is more stable and secure than Windows. :)

---

