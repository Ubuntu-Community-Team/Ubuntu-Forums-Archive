---
title: "How to Convert a Link into One Word or Phrase"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-04-07
:KS  My son uses a Mac and, when in an e-mail he sends me a link to something, the link appears, generally, as the word "here" (without the quotes but it shows up in blue) and, when I click on that word, it takes me to the link desired.

Is there some way in Ubuntu 8.10 that I can do the same thing? If so, please tell me which program(s) I will need and rough instructions as to how I should manipulate a link so that, in an e-mail I send to him, the link can appear as a word or phrase of my choice and still be a fully functional link.

Any help will be most appreciated. Thanks much.

Lawrence ):P

---

### Post by jpoRS on 2009-04-07
It has very little to do with what computer you use, and what software you use.  Unless you have a super-basic e-mail program you already can do it.

Usually there is a button (here on the forums it is a globe with some chain under it, get it, "link").  You kind find the Ubuntu forums one between the increase indent button and  the "remove link" button (chain with red X).

Depending on what program you are using, you can usually highlight whatever you want to make a link, go to File>Insert>Insert Link (or something like that) and it will give you a little pop-up for the URL you want to link.  Pretty simple.

I know those may sound confusing, but if you need help, let me know.

Good luck!
jim

---

### Post by WRDN on 2009-04-07
What you are referring to is a [hyperlink]("http://en.wikipedia.org/wiki/Hyperlink"). Most email packages/ websites have a button you can click to add hyperlinks. For example, on these forums, you highlight a word, then click the "Insert Link" button (with the icon of the earth and a link).

---

### Post by northern lights on 2009-04-07
Common email apps support this, even most webmail services actually do.

I'd suggest you either use the pre-installed email client *evolution* or install the more feature-rich *thunderbird*.

Evolution is found under *Applicatiuons > Internet* in the gnome menu, so will be thunderbird after installation.

Thunderbird can be installed from the *Add/Remove* dialog, the Synaptic Package Manager as well as from the commandline. Choose as you please. For the sake of ease of explanation, this is what you'd have to run from the terminal (*Applications > Accessories*) to install thunderbird:```
sudo apt-get install thunderbird
```Followed by your password (type it in, nothing will be displayed, hit Enter).

Reply with some info on your email service and so forth if you need help with configuring either client.

Evolution might do for you, thinderbird'd be my choice.

---

### Post by lhb1142 on 2009-04-07
> **jpoRS said:**
> It has very little to do with what computer you use, and what software you use.  Unless you have a super-basic e-mail program you already can do it.

Usually there is a button (here on the forums it is a globe with some chain under it, get it, "link").  You kind find the Ubuntu forums one between the increase indent button and  the "remove link" button (chain with red X).

Depending on what program you are using, you can usually highlight whatever you want to make a link, go to File>Insert>Insert Link (or something like that) and it will give you a little pop-up for the URL you want to link.  Pretty simple.

I know those may sound confusing, but if you need help, let me know.

Good luck!
jim

:KS  I am using Firefox 3.0.8. I do not see Insert->Insert Link under File. All I see is "Send Link." For that matter I don't even see the globe with a chain anywhere on this site!

I am using Yahoo! Mail and I generally use plain text to send my messages. I tried "converting" a link by right-clicking (there was no option present) and by looking in File but had absolutely no luck. I tried it in both plain text and rich text. I just don't seem to know what to look for or I am just not finding it.

I'm sure it's an easy process but I'll be darned if I can figure it out! Can you give me a step-by step? Thanks! ):P

---

### Post by nandemonai on 2009-04-07
> **lhb1142 said:**
> :KS  I am using Firefox 3.0.8. I do not see Insert->Insert Link under File. All I see is "Send Link." For that matter I don't even see the globe with a chain anywhere on this site!

I am using Yahoo! Mail and I generally use plain text to send my messages. I tried "converting" a link by right-clicking (there was no option present) and by looking in File but had absolutely no luck. I tried it in both plain text and rich text. I just don't seem to know what to look for or I am just not finding it.

I'm sure it's an easy process but I'll be darned if I can figure it out! Can you give me a step-by step? Thanks! ):P

Here's the html code for a link. Not sure if it works directly in Yahoo but it should.
```
<a href="http://insertaddresshere/">Insert Text Here</a>
```

---

### Post by batharoy on 2009-04-07
In yahoo mail switch to "Rich Text" highlight the word or phrase you wish to make a link from.
Click on the chain/globe next to the smiley with sunglasses.
insert the address in the box that pops up.

---

### Post by t0p on 2009-04-07
> **lhb1142 said:**
> :KS  I am using Firefox 3.0.8. I do not see Insert->Insert Link under File. All I see is "Send Link." For that matter I don't even see the globe with a chain anywhere on this site!

I am using Yahoo! Mail

Are you using the "new" look or the "classic" look?  I've got my yahoo mail open on another tab, in "classic" look when composing mail there is a row of icons along the top.  One of these is a globe and chain.  That's the link button.

I assume you're using the "new" look and advise you move back to "classic" asap!

---

### Post by lhb1142 on 2009-04-07
> **nandemonai said:**
> Here's the html code for a link. Not sure if it works directly in Yahoo but it should.
```
<a href="http://insertaddresshere/">Insert Text Here</a>
```

:KS Nope this does not work in Yahoo, either in plain text or rich text. I'm just going to give this up as a bad job.

Thanks for all the help given here even if nothing worked for me.

Lawrence ):P

---

### Post by anjilslaire on 2009-04-07
> **lhb1142 said:**
> :KS Nope this does not work in Yahoo, either in plain text or rich text. I'm just going to give this up as a bad job.

Thanks for all the help given here even if nothing worked for me.

Lawrence ):P

Try this:

Check the screenshot, it's taken from my Yahoo! account. Look where the curser is in the image, on a button of a globe & link.

Highlight the text you want to be a link, then click that button and follow along.

---

### Post by joeashcraft on 2009-04-07
Found a Yahoo-specific how to on _[about.com]("http://email.about.com/cs/yahoomailtips/qt/et101703.htm")_. Does this help?


[LIST]
[*]_[Make sure rich-text editing is enabled]("http://email.about.com/cs/yahoomailtips/qt/et071901.htm")_.
[*]Highlight the text that should point to the page you are linking to.
[*]Press the *Create Hyperlink* button in the formatting toolbar.
[*]Type or paste the desired URL.
[*]Click *OK*.
[/LIST]

---

