---
title: "Recent places in Natty"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by bob brazie on 2011-05-01
I have always found the recent places and the ability to clear all recent documents in previous versions.

It used to appear under the "places" in the top panel. I cannot find this in 11.04 and am wondering if it is even available anymore.

I did a Google search and could not find an answer.

Can someone shed any light on this for me?

Thanks in advance, Bob.

---

### Post by JayD2 on 2011-05-01
Go to your home folder (or any nautilus folder really). Mouse over the top task bar towards the left side and find the 'go' drop down menu. At the bottom you'll find your recent places and an option to clear history.

I do not know if or where recent documents are shown.

---

### Post by bob brazie on 2011-05-02
Thanks for the information. I did as you say and found the Go/clear history.

When I click on it there is a confirmation box where I click "clear".

When I check the files & folders lens they are still shown in the top "recent" area.

Might this be a bug?

---

### Post by 3rdalbum on 2011-05-02
> **bob brazie said:**
> Thanks for the information. I did as you say and found the Go/clear history.

When I click on it there is a confirmation box where I click "clear".

When I check the files & folders lens they are still shown in the top "recent" area.

Might this be a bug?

It's kind of like a bug - more like an inconsistency.

Nautilus (the file manager) is offering to clear the Gnome history. Unity (which provides the files and folders lense) doesn't use the Gnome history - it uses Zeitgeist these days, which operates in a different way.

The intended behaviour for Nautilus is to clear the Gnome history and the intended behaviour for Unity is to ignore the Gnome history and use Zeitgeist.

So yes, it's a bug, but only one applicable to the Ubuntu project as the component parts are doing exactly what they've been programmed to do. Would be a good idea to raise it against the "nautilus" package on Ubuntu, if it hasn't already been raised.

Unfortunately I can't solve your base problem of removing the Zeitgeist history for those files; maybe Google could give you instructions for blacklisting directories from Zeitgeist, but the nice easy GUI way is not available yet.

---

### Post by bob brazie on 2011-05-02
Interesting......

The information must be kept in a file or folder somewhere locally. But I can't find it.

I guess I can't mark this as "solved" though.

Thanks. Bob.

---

### Post by originion on 2011-05-12
To clear recent documents in Unity interface of Ubuntu Natty 11.04 use the following command in terminal::

```
rm ~/.local/share/zeitgeist/activity.sqlite zeitgeist-daemon --replace
```For in depth info of the issue you guys may view at this link:
[http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html](http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html)

Hope this helps. :D

---

### Post by r-senior on 2011-05-12
> **originion said:**
> ```
rm ~/.local/share/zeitgeist/activity.sqlite zeitgeist-daemon --replace
```
Just to avoid confusion (and I realise the link shows it), that is two separate commands:

```

rm ~/.local/share/zeitgeist/activity.sqlite 
zeitgeist-daemon --replace

```

and you may need to log out and log back in to see the result. History will then start to accumulate again.

---

### Post by bob brazie on 2011-05-12
Two commands?

May I ask what is done with the word "replace"? With what?

Thanks.

---

### Post by geazzy on 2011-05-12
> **r-senior said:**
> Just to avoid confusion (and I realise the link shows it), that is two separate commands:

```

rm ~/.local/share/zeitgeist/activity.sqlite 
zeitgeist-daemon --replace

```

and you may need to log out and log back in to see the result. History will then start to accumulate again.

I am still confused where I could see Recent hystory... :D

---

