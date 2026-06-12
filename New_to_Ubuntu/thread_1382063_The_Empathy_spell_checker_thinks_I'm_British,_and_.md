---
title: "The Empathy spell checker thinks I'm British, and I'm not."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by jon.reeve on 2010-01-15
How do I change the language of the spell checker in Empathy? My system language is set to American English, and has been working fine, but somehow Empathy thinks I'm British. Every time I type "flavor" without a "u," I'm told I'm misspelling it. The settings in Empathy only list "English" as an available language.

---

### Post by Paqman on 2010-01-15
> **jon.reeve said:**
> Every time I type "flavor" without a "u," I'm told I'm misspelling it.

That's because you are. And all your countrymen, too ;)

Some believe this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/445863"), rather than a feature however.

---

### Post by d3v1150m471c on 2010-01-15
Meh... i didn't care for empathy. Try pidgin. pidgin has some really cool plugins for it too you can find by searching pidgin in synaptic. Then under tools you can configure these.

---

### Post by scratman on 2010-01-15
I don't know how exactly to fix the bug, but I imagine that there is a possibility to download new dictionaries from the website.

<rant>
With regard to our apparent misspelling of flavour, please bear in mind that America has been copying English badly for far less time than England has been using it as a native tongue.  Please also bear in mind that America was no more than a few votes away from speaking Spanish, which would have made life very easy for your Mexican cousins.

I have no objection to Americans speaking English, after all, we could hardly expect you to make up a new language of your own.   I just wish the lazy kid who didn't do the work and copied it off a friend had done so more proficiently.
</rant>

---

### Post by audiomick on 2010-01-15
+1 <rant>;)
I have the irritation with other things in the other direction. Spell checkers trying to force me to use US American "English" and I **don't want to!!!**

---

### Post by d3v1150m471c on 2010-01-15
lol p i d g i n ;) check out my above post. good luck to you.

---

### Post by mister_playboy on 2010-01-16
These annoyances come from the fact Canonical is based in the UK.  [[COLOR="Blue"]A sizable majority of native English speakers live in the USA[/COLOR]](http://en.wikipedia.org/wiki/File:English_dialects1997_modified.svg), so we have a valid complaint. ;)

---

### Post by Paqman on 2010-01-16
> **mister_playboy said:**
> These annoyances come from the fact Canonical is based in the UK.

Empathy is a Gnome app, it's not maintained by Canonical.

---

### Post by joslin on 2010-07-08
Whatever, the Brits are stubborn to modernizing their language so they can cheat at Scrabble.  

(ie. thru vs. through, color vs colour, aluminum vs aluminium, etc)


But seriously, is there a fix for this?  It drives me crazy.

---

### Post by cbanbury on 2010-09-07
I have the opposite problem, My empathy keeping trying to put extra z's everywhere! I don't have a problem with American English on the whole, but you really can't get away with spelling laser with a z... 

Anyone figured this out yet?

---

### Post by migs73 on 2010-09-07
+1 on the laser. Light Amplification by Ztimulated Emission of Radiation? I don't think so! And I'm not even English!

---

### Post by col48 on 2010-09-07
American and British spellings were standardised by different dictionary compilers.  And I think the country with the largest number of people who use English in everyday life is probably India, where it is one of the official languages.

Spell checkers should probably accept both US and UK versions - with the way the educashun sistims are goin in both contrys theyll be the same anyway in 50 yeers.

---

### Post by ryor310575 on 2010-09-24
Try "System->Administration->Language Suport" Install & Set the language

---

### Post by cooltd825 on 2010-10-21
I used to open Gconf editor and manually change the /app/empathy language value from "en" to "en-US".  that would always do the trick.

but unfortunately, the "empathy" is missing.  I'm not sure as to why, it just doesn't exist in 10.10 anymore.  any ideas?

---

### Post by Berrex on 2010-10-26
There's a configuration entry in dconf-editor for empathy, which you can get to by installing dconf-tools, launching dconf-editor, and then browsing to apps &#8594; empathy &#8594; conversation. There's an entry called "spell-checker-languages" with a value of "en." Changing this to "en-us" would do the trick, I'm sure, except for one problem: that field cannot be changed.

So yeah, I'm stuck. Guess I'll just be using Pidgin. It's especially bothersome when Empathy marks words like "mom" as misspelled and offers no option to add it to the dictionary or ignore the spelling "error"&#8230;

---

### Post by Richard Clowes on 2010-10-26
Payback for the microsloth spell checker that tries to force everyone to use americun spelling whether you come from that cuntry or not.

We used to lose marks at uni if we used American spelling, so the answer is to learn to spell and turn the spell checker off. Works a treat.

---

### Post by nutznboltz on 2011-05-17
Click on "Applications" in the Dock.
Type Language in the text field at the top
Click on Language Support (blue UN flag)
If you are asked about installing more software do it.
Fiddle with the controls until you have the language you want and click:
Apply System Wide.
Reboot or re-login?

Hmm. still broken.  Plus now I'm having bad reactions between Unity and Empathy: the main Empathy window closes for no apparent reason and can't be reopened without restarting Empathy.

---

### Post by beew on 2011-05-17
Spell Checkers always assume I am American but I am not. :)

---

### Post by nutznboltz on 2011-05-17
What a neat forum. People come here with real software issues only to be sassed at because of what country they were born in.

---

### Post by Allavona on 2011-05-17
It really makes no difference what country you are from. People want their spell checkers to work for their respective language.  Is that really too much to ask?

> What a neat forum. People come here with real software issues only to be sassed at because of what country they were born in. 	

Agreed. 

Also, the United States has no official language. People are FREE to speak, read and write whatever language floats their boat.

> Payback for the microsloth spell checker that tries to force everyone to  use americun spelling whether you come from that cuntry or not.

We used to lose marks at uni if we used American spelling, so the answer  is to learn to spell and turn the spell checker off. Works a treat. 	

Learn to spell! LOL

Bottom Line. We are all here to help and learn from one another. This cannot be accomplished if we engage in needless banter about linguistics, origins, etc...

Oh! And like C3PO, I am (thanks to Google Translate) well versed in over 200 forms of communication!!!!:)

---

### Post by flomar on 2011-05-23
Do I get this right? To get Empathy using a different language for spellchecking I have to apply this language systemwide??

My native language is german. 
However I'd like my system to be in english
I live in Spain (catalonia) at the moment, therefore I write a lot of spanish and catalan.
Why can't empathy work with all theses 4 languages at a time, like Chrome manages perfectly?!

---

### Post by mastablasta on 2011-05-23
it's the linux DE way of doing things.
 
on a side note for example to force gimp to use the language of your choice (by default it uses system language as well) in windows you do it by deleting all other language files from GIMP folder. stupidest solution ever! yes oyu can't switch the language well unless you remove all other languages then it is happy to switch.
 
but it might be something similar in this case. only it oculd be more difficult since files oculd be systemwide.
 
I think it's the same thing with time and email time stamps... since in Europe (and large part of the world) uses day first and then month i had to change it to british english.

---

### Post by btindie on 2011-11-16
I'm another one that has the opposite problem. My system is configured  for British English but yet Empathy gives me american spelling  suggestions. i.e. I type colour and it thinks it's incorrect. It also  wants to put a 'z' in everything... I'm using 10.10

The only language option given under Empathy is 'English', is this supposed to mean English English or American English?

It uses the correct message translations as seen by lsof - /usr/share/locale-langpack/en_GB/LC_MESSAGES/empathy.mo

I read in this [thread]("http://ubuntuforums.org/showthread.php?t=993377")  that empathy uses aspell internally for it's spell checking. When I use  aspell manually it works correctly but doesn't through empathy even if I  set "lang en_GB" ins ~/.aspell.conf. Is there a way to force empathy to  use the correct language?

---

### Post by grahammechanical on 2011-11-16
I would like to counter this comment: 

> These annoyances come from the fact Canonical is based in the UK

with this link to the Ubuntu documentation style guide:

[https://wiki.ubuntu.com/DocumentationTeam/StyleGuide/SpellingPunctuationGrammar]("https://wiki.ubuntu.com/DocumentationTeam/StyleGuide/SpellingPunctuationGrammar")

Note this comment under Spelling:

> Use standard American English spelling in all Ubuntu English language documents.

Regards.

---

### Post by winjeel on 2011-11-18
> **audiomick said:**
> +1 <rant>;)
I have the irritation with other things in the other direction. Spell checkers trying to force me to use US American "English" and I **don't want to!!!**

I second that. It is called linguistic imperialism (I'm sure there is a wikipedia page on it). And in MS Word it's not just the spell checker, it's also the grammar checker, too.

---

### Post by cemelie on 2011-11-22
> **winjeel said:**
> I second that. It is called linguistic imperialism (I'm sure there is a wikipedia page on it). And in MS Word it's not just the spell checker, it's also the grammar checker, too.

Third that! Every grammar checker I've tried are targeted for American English users, including this [grammar checker]("http://www.gingersoftware.com/features/grammar_checker.html") which I've shortlisted to purchase for my son (only to know that it corrects my colour to color).

---

