---
title: "The Chromium Browser?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-16
Someone here explained the difference between Chromium and Google's Chrome browser. As I understand it, Chromium is the open source project and Chrome is Google's application of the project.

I'm very impressed with the Chrome browser, and I think other people are too. However, I would prefer a proper deb type installation via a repository and I'd prefer it to be devoid of all the Google paraphernalia about collecting personal information.

Is there such a thing as a Chromium deb for downloading without having to compile the source code on my machine?

---

### Post by Paqman on 2009-12-16
> **Roger Allott said:**
> 
Is there such a thing as a Chromium deb for downloading without having to compile the source code on my machine?

Better still, there's a [PPA]("https://launchpad.net/~chromium-daily/+archive/ppa"). To add the PPA:
```
sudo add-apt-repository ppa:chromium-daily
```

Put the above into a terminal, enter your password and you'll be subscribed to the Chromium developers' daily builds of Chromium. You'll be able to install through any of the normal package management tools (eg: Software Centre, Synaptic) and you'll get all the updates automatically.

---

### Post by rajeev1204 on 2009-12-16
> **Roger Allott said:**
> Someone here explained the difference between Chromium and Google's Chrome browser. As I understand it, Chromium is the open source project and Chrome is Google's application of the project.

I'm very impressed with the Chrome browser, and I think other people are too. However, I would prefer a proper deb type installation via a repository and I'd prefer it to be devoid of all the Google paraphernalia about collecting personal information.

Is there such a thing as a Chromium deb for downloading without having to compile the source code on my machine?

Google opened the code to chrome and called it the chromium project.Chromium also has code from mozilla and apple's webkit.

But like any open source project, chromium is a project and chrome is a product of google.

The launchpad PPA is the chromium browser, not chrome.That PPA will have continuous updates,some good some bad ,some real ugly since its a testbed for development.
Chrome on the other hand will have stages like alpha,beta and considering google's style of releases, will be beta for a long time.So updates will be more stable and tested by google themselves probably before it comes to you.

Chrome belongs to google and has some licenses which apply unlike chromium which belongs to the community .

---

### Post by Roger Allott on 2009-12-16
> **Paqman said:**
> Better still, there's a [PPA]("https://launchpad.net/~chromium-daily/+archive/ppa"). To add the PPA:
```
sudo add-apt-repository ppa:chromium-daily
```

Put the above into a terminal, enter your password and you'll be subscribed to the Chromium developers' daily builds of Chromium. You'll be able to install through any of the normal package management tools (eg: Software Centre, Synaptic) and you'll get all the updates automatically.

Excellent! Thanks for that. I'm now writing this from Chromium, which looks pretty much identical to Chrome from what I can see thus far.

---

### Post by Paqman on 2009-12-16
> **Roger Allott said:**
> Excellent! Thanks for that. I'm now writing this from Chromium, which looks pretty much identical to Chrome from what I can see thus far.

It is. Chrome is just Chromium with Google branding. As rajeev1204 mentioned, this will be potentially more unstable than the official Google release. Expect an update every day, some of which can cause borkage, although from my own experience with Chromium it was pretty good.

---

### Post by mkvnmtr on 2009-12-16
There is also a branch of Chromium called Iron. It removes everything that they feel is invasive of privacy.

---

