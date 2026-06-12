---
title: "About VIM: 'linebreak' and new lines"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by crowhill on 2009-11-12
Hi there

I have the following example of code showing up in VIM ('linebreak' is on):

```
<div>
    bla bla bla bla bla bla
bla bla bla bla bla
</div>
```

where the new line is showing up because of a line break at the end of the first line. However, I want it to look like this:

```
<div>
    bla bla bla bla bla bla
    bla bla bla bla bla
</div>
```

I know, I can do that by typing <Return> at the end of the line (with 'autoindent' on). It would be much better though if it did that automatically. The Windows editor Crimson does it, for example. Is there a way to set up the file **.vimrc** such that VIM thinks of a new line after a line break (following a <Tab>) as new physical line?

If I put

> set showbreak=/ / / / 

in my **.vimrc** I almost get what I want. The problem is that it does the shifting to the right after *every* linebreak and not only after those that follow at the end of a line that begins with a <Tab>.

In short, I want to put something like

```
if 'beginning of line = <Tab>'
then 'set showbreak=/ / / / '
```

in my **.vimrc**. How could that be done?

Thank you very, very much. This is really bothering me.

Cheers,
crowhill.

---

