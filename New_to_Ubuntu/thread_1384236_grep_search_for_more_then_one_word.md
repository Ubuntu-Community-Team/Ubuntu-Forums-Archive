---
title: "grep search for more then one word"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ja660k on 2010-01-18
hey guys, 
im writing an conky script that displays the last 5 tweets i got in twitter.
but im stuck at grep, i need it to search on more then one keyword 

here is the bash i have so far

```

#!/bin/bash

# my twitter timeline xml
URI=http://twitter.com/statuses/friends_timeline/32346344.xml

# number of tweets
tweets=5

#username and password
user=XXXX
pass=XXXX

# execute
wget -O - \
--http-user $user \
--http-password $pass \
$URI | grep text |\
sed -e :a -e 's/<[^>]*>//g;/</N' |\
sed -e 's/[ \t]*//' |\
sed -e 's/\(.*\)/ \1/' |\
sed -e 's/\.//' |\
sed -e 's/\"//' |\
sed -e 's/\"//'

```

where grep needs to search for EXACTLY <text> and <screen_name>

any help would be appreciated.
thanks in advance

---

### Post by Silent Warrior on 2010-01-18
Hm. Bash-ignorant to the max, here, but could you do the check and a new grep as a second pass? Like,
```
$URI | grep text |\
$URI | grep screen_name |\
```
I confess again that I know not even half as much about bash as I would need to even contemplate such a script. (Well, it's mostly the sed-squigglies I don't get - I actually managed to set up a script that successfully updated something from SVN and had it compile once. Actually using that script, though, is more fuss than doing without. Much typing.)

---

### Post by ja660k on 2010-01-18
unfortunatly that didnt work
because it will filter out everything but <text> so <screen_name> will never be found, or the other way around 

i just accidentally found the solution... you were on a more right track then me, but instead of calling grep twice but telling grep to match 2 patterns:
```
 wget http://example | grep -e text -e screen_name 
```
like that seemed to do the trick.

thankyou, if it wasnt for you i wouldnt of tried it that way

---

