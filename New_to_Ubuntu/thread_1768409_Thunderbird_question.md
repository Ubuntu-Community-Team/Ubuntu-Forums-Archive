---
title: "Thunderbird question"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by e.jejcic on 2011-05-26
******Well.I have a funny problem when I want to write an e-mail. The thing is that I have the adress  (e-mail address) written right in the adress book, but when I write an e-mail in the "to" box appears the user name beetwen quote marks. So when I send it I got an error saying "is not a true e-mail adress". I wonder if somebody took my Thunderbird and made some whatever. I wonder if this can be fixed. Sorry my english is not good. Anyway I appreciate any repply. Thank's in advance from Eduardo.

---

### Post by wolfen69 on 2011-05-26
One way to fix it would be to delete your .thunderbird config file. But then you would have to set up your email accounts all over again.

---

### Post by e.jejcic on 2011-05-26
I really appreciate your fast response. I will try that and see what happend. Thank you very much. Regards from Eduardo.

---

### Post by SeijiSensei on 2011-05-26
Valid e-mail addresses consist of a "name" part and an "address" part.  So my address might be 

```
John Smith <jsmith@example.com>
```

However if the name includes any special characters like a period or an apostrophe, it must be enclosed in quotation marks like these:

```
"John W. Smith" <jsmith@example.com>
"John O'Donnell" <jodonnell@example.com>
```

Addresses like these are perfectly valid and are automatically rendered correctly by Thunderbird in the From/To/Cc fields.  If that's the format of your problematic "To" address, your mail provider is clueless.

If you're in a country where single quoting is the norm, you need to "escape" any apostrophes like this:

```
'John O\'Donnell' <jodonnell@example.com>
```

Personally I'd just use double quotes in every case to avoid this issue.

---

### Post by SoFl W on 2011-05-26
If it is in your address book, right click or select properties and see if the mistake is in the actual address.

---

### Post by e.jejcic on 2011-05-27
Good morning Sirs I read the last two post. Now I'm tottaly lost.The actual adress I tried to write to is jejcic@arnet .com.ar and in the "to" box appears as "jejcic"@arnet .com.ar and the adress in adress book is written jejcic@arnet .com.ar So I don't know what I am doing wrong and what to do next.Thanks from Eduardo.

---

### Post by nosehat on 2011-05-27
You may want to delete this email address from your address book, then retype it in.

It's possible that one of the letters in jejcic was accidentally entered as a special character when you first added this address, so Thunderbird is putting quotes around it?  I'm not sure if that will help, but it's what I'd try next.

---

### Post by e.jejcic on 2011-05-27
Well............. Nosehat you are a Genius, thak you very much.I'm going to mark this thread as solved. What I did was to retype the adress in the adress book ( anyway was written right).And when I tried to write an E-mail the adress was shown right (without the quote marks)  This forum is amasing.Thank's to all of you. Regards from Argentina.

---

