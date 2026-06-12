---
title: "Thunderbird folder - wrong name"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by col48 on 2011-03-06
Documenting a problem and its solution.

New Thunderbird (T3) but with all its files migrated from the old one (T2).

The list of folders had two folders labelled 'Outbox' and none labelled 'Unsent Messages'.  This had not been the case on T2, which had one of each.  At the time both folders were (and should have been) empty.

Focussing on each folder in thunderbird and right-clicking to check on properties, the two were distinct as the locations were different.  (NB the difference was only visible by scrolling the entry to see the RH end of it).  One was at ..../Outbox  and the other at ..../Unsent Messages.

So it's only the labels which are wrong.

Remedy (this text assumes the above situation, but change the names and it should be just as good)

1. Close Thunderbird.
2. Backup .thunderbird (T3) or .mozilla-thunderbird (T2)
3. Restart the computer. I am not sure how important this is but I think it may be essential not to have thunderbird in memory or cache by the time you get to step 7.
4. navigate to your Local Folders folder in your file browser:
(you'll need to choose to show hidden files to see .thunderbird)
```
~/.thunderbird/xxxxxxxx.default/Mail/Local Folders
```
** xxxxxxxx is a random 8-character string and matches the one in profile.ini in the same folder - you've probably only got one file with this pattern anyway.
** For T2 it starts ~/.mozilla-thunderbird 
5. In a file editor such as emacs or gedit (NOT a Word Processor) open the file 'Unsent Messages.msf' in this folder (without the quotes!)
** This file has the .msf suffix.  The one without contains the actual messages, if any.
6. Most of this file will be human-readable but unintelligible.  However, somewhere around lines 25-30 you will find the string 'Outbox' - again, without the quotes.  Change this to 'Unsent Messages' (no quotes, and the space is acceptable) and save the file.  [COLOR="Red"]Be very careful not to change anything else in the file[/COLOR].
7. Now Open Thunderbird and the folder should have its proper name.

---

### Post by maqtanim on 2011-03-06
Thanks for sharing!
:popcorn:

---

