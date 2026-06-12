---
title: "search and replace across multiple files"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Stoneface on 2010-01-16
I would like to search for <? in all files in folder and replace them by <?php so I do not have to worry about these short tags in these php files anymore. I think I could do this with find and sed. But as I am a beginner in this area some help would be appreciated.
I was thinking about editing the follwing command:
```
find ./ -type f -exec sed -i 's/\<?/\<?php/' {} \;
```
I think the folder to search in is missing. Any ideas how to tell to search in folder /a/b/c/ ?

Another option I found was
```
find ./ -type f | xargs perl -pi -w -e 's/SEARCH/REPLACE/g;'
```

Which one would be better?

---

### Post by Stoneface on 2010-01-16
Found one command line option [here]("http://stackoverflow.com/questions/684587/batch-script-to-replace-php-short-open-tags-with-php") just for replacing short tags by <?php :```
find . -iname "*.php" -print0 | xargs -0 -I{} sed -i 's/\(<\?\)\([^a-zA-Z]\)/\1php\2/g' '{}'

```

I will try it later - after backing up all - and will post the outcome as soon as possible.

---

### Post by kaibob on 2010-01-16
> **Stoneface said:**
> I would like to search for <? in all files in folder and replace them by <?php so I do not have to worry about these short tags in these php files anymore. I think I could do this with find and sed. But as I am a beginner in this area some help would be appreciated.
I was thinking about editing the follwing command:
```
find ./ -type f -exec sed -i 's/\<?/\<?php/' {} \;
```
I'm think the folder to search in is missing. Any ideas how to tell to search in folder /a/b/c/ ?
<snip>

I'm not certain what you mean by the above, but to search in directory /a/b/c just change ./ to /a/b/c. 

If you are only going to change files in one directory only, you do not have to use find. I would use the following because it is simpler:

```
for file in * ; do sed -i 's/<?/<?php/g' "$file" ; done
```

---

### Post by Stoneface on 2010-01-16
When I ran the command I got:

```

$ sudo for file in * ; do sed -i 's/<?/<?php/g' "$file" ; done
-bash: syntax error near unexpected token `do'

```

---

### Post by kaibob on 2010-01-16
> **Stoneface said:**
> When I ran the command I got:

```

$ sudo for file in * ; do sed -i 's/<?/<?php/g' "$file" ; done
-bash: syntax error near unexpected token `do'

```

Why are you attempting to run the command with sudo? Normally, there is no reason to do that.

---

### Post by Stoneface on 2010-01-17
Didn't know that. Thanks for all the help so far. 
Here is the result without sudo:
```
$ for file in * ; do sed -i 's/<?/<?php/g' "$file" ; done
sed: 1: "404.php": invalid command code .
sed: 1: "admin": command a expects \ followed by text
sed: 1: "archive.php": command a expects \ followed by text
sed: 1: "archives.php": command a expects \ followed by text
sed: 1: "comments.php": command c expects \ followed by text
sed: 1: "css": command c expects \ followed by text
sed: 1: "footer.php": invalid command code f
sed: 1: "functions.php": invalid command code f
sed: 1: "header.php": extra characters at the end of h command
sed: 1: "image.php": command i expects \ followed by text
sed: 1: "image_resize.php": command i expects \ followed by text
sed: 1: "images": command i expects \ followed by text
sed: 1: "index.php": command i expects \ followed by text
sed: 1: "js": invalid command code j
sed: 1: "links.php": extra characters at the end of l command
sed: 1: "page.php": extra characters at the end of p command
sed: 1: "screenshot.png": unterminated substitute pattern
sed: 1: "scripts": unterminated substitute pattern
sed: 1: "search.php": unterminated substitute pattern
sed: 1: "searchform.php": unterminated substitute pattern
sed: 1: "sidebar.php": unterminated substitute pattern
sed: 1: "sidebar_bottom.php": unterminated substitute pattern
sed: 1: "simple_recent_comments.php": unterminated substitute pattern
sed: 1: "single.php": unterminated substitute pattern
sed: 1: "style.css": unterminated substitute pattern
sed: 1: "template_CONTACT.php": undefined label 'emplate_CONTACT.php'
sed: 1: "template_PROFILE.php": undefined label 'emplate_PROFILE.php'
sed: 1: "template_TESTIMONIALS.php": undefined label 'emplate_TESTIMONIALS.php'
sed: 1: "template_WORK.php": undefined label 'emplate_WORK.php'
sed: 1: "twitter.php": undefined label 'witter.php'
sed: -i may not be used with stdin
sed: -i may not be used with stdin

```

---

### Post by Stoneface on 2010-01-17
So I added an extensionfor -i and:

```
 for file in * ; do sed -i '.bak' 's/<?/<?php/g' "$file" ; done
sed: admin: in-place editing only works for regular files
sed: css: in-place editing only works for regular files
sed: images: in-place editing only works for regular files
sed: js: in-place editing only works for regular files
sed: scripts: in-place editing only works for regular files

```

.baks were created which is good as when I went to my localhost and tested one of the files I got:

```
Parse error: syntax error, unexpected T_INCLUDE in /path/to/functions.php on line 2
```

In that file I found <?phpphp at the top. So the for do done command created some erroneous PHP starter tags. Many <?php were replaced by <?phpphp while I only needed to replace <? by <?php

---

### Post by kaibob on 2010-01-17
Unfortunately, my knowlege of sed is quite limited. Perhaps another forum member will be able to help. 

If you do not get any responses, you may want to request that a moderator move this thread to the Programming Talk forum. The forum members there are very knowledgeable and helpful, and this is easy stuff for them. To ask that the thread be moved, just click on "Report Abuse" in the lower left corner of your post.

Sorry I couldn't help.

---

### Post by Stoneface on 2010-01-17
> **kaibob said:**
> Unfortunately, my knowlege of sed is quite limited. Perhaps another forum member will be able to help. 

If you do not get any responses, you may want to request that a moderator move this thread to the Programming Talk forum. The forum members there are very knowledgeable and helpful, and this is easy stuff for them. To ask that the thread be moved, just click on "Report Abuse" in the lower left corner of your post.

Sorry I couldn't help.

Thanks for all the help Kaibob. I will ask the moderator to move the thread to programming as soon as I have figured out how

---

### Post by sakibmoon on 2012-02-05
> **kaibob said:**
> I'm not certain what you mean by the above, but to search in directory /a/b/c just change ./ to /a/b/c. 

If you are only going to change files in one directory only, you do not have to use find. I would use the following because it is simpler:

```
for file in * ; do sed -i 's/<?/<?php/g' "$file" ; done
```

Thanks, man. That saved the day. It's simpler and effective.

---

