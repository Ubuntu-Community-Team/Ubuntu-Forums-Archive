---
title: "Search scripts; what editor do I need for these characters?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by ankspo71 on 2010-01-03
Hi,

Below is a working (but still amateurish) html "mirror search" script I have copy pasted together as I still learn how to create them. I never could figure out how to put a "phrase" inside quotes until today. Up until now, I haven't been able to add phrases wrapped in quotes, because value=""example phrase"" simply doesn't work for me.

Here's the script:
```
<center>
<form method="GET" action="http://www.google.com/search?q=">
<input name="q" size="40" maxlength="255" type="hidden" value="inurl:(mirror|ftp)">
<input name="q" size="40" maxlength="255" type="hidden" value="+intitle:index.of">
<input name="q" size="40" maxlength="255" type="hidden" value="+&#8221;last modified&#8221;">
<input name="q" size="40" maxlength="255" type="hidden" value="+&#8221;parent directory&#8221;">
<input name="q" size="40" maxlength="255" type="text" value="Mirror Search">
<input name="q" size="40" maxlength="255" type="hidden" value="-htm -html -php -asp">
<input name="q" size="40" maxlength="255" type="hidden" value="">
<input name="" value="SEARCH" type="submit">
</form>
</center>
 
```What I would like to know is, what kind of editor do I need to make both** " **and **&#8221;** characters. Do I need an html, or javascript, or maybe a php editer? Also, what is the other 'quotation mark' called?
Thanks,
James

---

### Post by ankspo71 on 2010-01-03
Hi Again,
I just wanted to add that I would like to use the quotes in my searches because "tree cutting service" gets more accurate results than (tree cutting service).

Although, when viewing the same page source in firefox the script appears as this:
```

value="+â&#8364;last modifiedâ&#8364;">
value="+â&#8364;parent directoryâ&#8364;">

```So I am wondering if this will cause problems between browsers or search engines.

I was unable to come up with anything in Synaptic, or by searching Google, or looking around in Gnome's Character Map.
I'll give the character map another look. I did find this though:
> [SIZE=6] 
[/SIZE]U+030B COMBINING DOUBLE ACUTE ACCENT

General Character Properties

In Unicode since: 1.1
Unicode category: Mark, Non-Spacing

Various Useful Representations

UTF-8: 0xCC 0x8B
UTF-16: 0x030B

C octal escaped UTF-8: \314\213
XML decimal entity: &#779;

Annotations and Cross References

Notes:
 &#8226; Hungarian, Chuvash

See also:
 &#8226; U+0022 QUOTATION MARK
 &#8226; U+02BA MODIFIER LETTER DOUBLE PRIME
 &#8226; U+02DD DOUBLE ACUTE ACCENTI don't see how an a&#779; accent would work in a search script though. Oh well lol. Until I find something I can keep copying and pasting the characters for now.
Thanks.

---

### Post by ankspo71 on 2010-01-03
Hi Again,
The problem is solved. I figured out I can use a space to create the[SIZE=3]**  &#779; **[/SIZE]character in the character map. It is located at Script > Inherited then (4 across, 2 down). This still leaves me copying and pasting the character though. I just added the character map to the panel with a custom entry. That should help me in the future.
Thanks.

---

