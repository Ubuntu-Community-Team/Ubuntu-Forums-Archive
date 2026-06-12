---
title: "rename syntax"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by expatCM on 2010-07-13
What I want to do is to rename all the .thm files in my photographs directory and all the sub directories. I do not want to move the files from their present directories.  I think the command to do this is as follows on the assumption that the new file extension will be .thx.

mv /photographs/*.thm /photographs/*.thx /R

I am very good at getting the syntax wrong.  Would someone please tell me how I did this time?

---

### Post by yaaarrrgg on 2010-07-13
There's a command named "rename" that might work better for you.  The syntax should be:

```
rename 'findpattern' 'replacewithstring' 'yourfiles'
```

For example:

rename .thm .thx *

You can try it on just one file if you are not sure.

---

### Post by expatCM on 2010-07-13
Thank you for telling me about the rename command, I did not know that it existed ....

I just took a look at the man page and ....  it needs a bit more detail.  It seems that the syntax is "rename Perl Expression Files".  So to translate that to your syntax "rename 'findpattern' 'replacewithstring' 'yourfiles'", the find pattern and replace with string are presumably Perl Expression Files?

So what you wrote in your example (rename .thm .thx *) was quite straight forward, the only thing missing for me is the switch to apply to all sub directories which I guess is by adding /s at the end of the string?

---

### Post by yaaarrrgg on 2010-07-13
ETA: it looks like rename on Ubuntu just takes a perl regular expression string.  It's in the form 's/find/replace/'.  

Hmm... I've never used a /s switch.  Is that for bash shell, or another? 

Generally if the command doesn't support a simple recursive flag, I make the commands recursive by sticking them in a find, like:

```
cd /to/your/path
find -exec rename 's/\.thm$/.thx/' '{}' ';'
```

The '{}' part is substituted with the found file name.  Sometimes that useful when a shell expansion like */* is too big.   The ';' just tells find that it's reached the end of the embedded command.

Also, I tightened up the regular expression so it should only match a . extension at the end of the file name.

For larger scripts you can pipe it to a variable like:

```
find /path/to/files/ | while read f
do
  echo "the file is $f"
done
```

---

### Post by kaibob on 2010-07-14
This will do what you want:

```
shopt -s globstar ; rename -v 's/.thm$/.thx/' **/*.thm
```

Be sure you are in the correct directory.

---

### Post by expatCM on 2010-07-14
oooopps ....  yes, my error.  I have just been helping someone with a dos command and there /s is for sub directories.  I did mean /R.

---

