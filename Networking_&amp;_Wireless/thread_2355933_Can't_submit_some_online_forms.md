---
title: "Can't submit some online forms"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by alex517 on 2017-03-18
I'm using Ubuntu 14.04.3 LTS. Some online forms don't submit. I've tried Chrome and Seamonkey. Nothing happens when I press the submit button. If I delete some required info, the data verification messages appear when I press submit, but if I fill that data in again and press submit = nothing.

The same forms submit without a problem on my Windows XP machine.

I don't have any examples, as the form it's most recently happened with is only available behind a login (the login form works without a problem).

I've seen this, but it doesn't help: [http://askubuntu.com/questions/189628/why-are-some-online-forms-unable-to-submit](http://askubuntu.com/questions/189628/why-are-some-online-forms-unable-to-submit) - I tried the ping commands, and
```
ping -s 1300 -M do google.com
```
came back as "truncated" - does that mean there's packet loss? If so, how can I fix that?

I'm not very technical in terms of Ubuntu.

---

### Post by ajgreeny on 2017-03-18
Are these form of the filetype pdf which open in the browser preview window?
I don't think you will get that to work, if that is the situation, but we will need a lot more detail of the specific forms that are giving you this problem if we are to help any further.

---

### Post by alex517 on 2017-03-18
Just regular HTML forms, with usual things like name, address etc.

---

### Post by SeijiSensei on 2017-03-18
Do you use an ad blocker or something like Ghostery or noscript?  All of those can interfere with forms that use scripts rather than simple HTTP POST uploads.

---

### Post by alex517 on 2017-03-19
> **SeijiSensei said:**
> Do you use an ad blocker or something like Ghostery or noscript?  All of those can interfere with forms that use scripts rather than simple HTTP POST uploads.

Thanks - that's something I should have mentioned. I don't in Seamonkey. I do in Chrome, but have tried in Incognito, which doesn't have any extensions.

---

