---
title: "Terminal copying"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-12-21
If i have two folders [./folder1] and [./folder2] and in folder1 i have two files [./folder1/file1] and [./folder1/.hiddenfile1] 

I want to use a terminal to copy the contents of folder1 into folder2 without copying the folder itself so i use [cp ./folder1/* ./folder2/] but that wont copy the hidden folder how do i modify this command to included hidden folders but still just the contents and not folder1 itself??

---

### Post by Grenage on 2009-12-21
I think the *recursive* option copies hidden files.

```
cp -r ./folder1/* ./folder2/
```

---

### Post by CaptainMark on 2009-12-21
> **Grenage said:**
> I think the *recursive* option copies hidden files.

```
cp -r ./folder1/* ./folder2/
```Seems to have no effect on hidden files

---

### Post by sisco311 on 2009-12-21
```
cp dir1/* dir1/.[!.]* dir2/
```

or

```
cp ./dir1/{*,.[!.]*} ./dir2/
```

---

### Post by USB_NL on 2009-12-21
I cant find it for you in [cp --help] maby you can?

ubuntu@ubuntu:~$ cp --help
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
  -a, --archive                same as -dR --preserve=**all** ***(<--is this it?)***
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
      --copy-contents          copy contents of special files when recursive
  -d                           same as --no-dereference --preserve=links
  -f, --force                  if an existing destination file cannot be
                                 opened, remove it and try again (redundant if
                                 the -n option is used)
  -i, --interactive            prompt before overwrite (overrides a previous -n
                                  option)
  -H                           follow command-line symbolic links in SOURCE
  -l, --link                   link files instead of copying
  -L, --dereference            always follow symbolic links in SOURCE
  -n, --no-clobber             do not overwrite an existing file (overrides
                                 a previous -i option)
  -P, --no-dereference         never follow symbolic links in SOURCE
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: context, links, xattr,
                                 **all** ***(<--is this it?)***
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behavior
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

Report cp bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>

---

### Post by CaptainMark on 2009-12-21
Getting closer, this works good for hidden files thanks, but also what about hidden directories i added a hidden directory inside folder1 and got a error message saying it would be ommited,

---

### Post by sisco311 on 2009-12-21
> **CaptainMark said:**
> Getting closer, this works good for hidden files thanks, but also what about hidden directories i added a hidden directory inside folder1 and got a error message saying it would be ommited,

Use the -r flag:
```
cp -r dir1/{*,.[!.]*} dir2/
```

---

### Post by CaptainMark on 2009-12-21
oh yeah, how i forgot thats standard cp behaviour,  ](*,) would you mind breaking this {*,.[!.]*} down a bit, its not too important but i like to understand what im doin so i can reapply next time if something similar comes up, thanks

---

### Post by sisco311 on 2009-12-21
> **CaptainMark said:**
> oh yeah, how i forgot thats standard cp behaviour,  ](*,) would you mind breaking this {*,.[!.]*} down a bit, its not too important but i like to understand what im doin so i can reapply next time if something similar comes up, thanks

{file1,file2,file3} is a comma separated list.
i.e.:
instead of:
```
ls /home/user/Music /home/user/Video
```
you can write:
```
ls /home/user/{Music,Video}
```

or 
```
ls {*,.[!.]*}
```
-> 
```
ls * 
ls .[!.]*
```

* matches any string (including the null string)

.* matches a string which starts with a period 

Every directory has two special files whose names consist of one and two periods: `..' refers to the parent of the current working directory, and `.' refers to the current working directory itself. If the current working directory is `/home/username', you can use `.' to specify `/home/username' and `..' to specify `/home'.

So .* will also match the current and parent directories.


[...] matches any one of the enclosed characters. if the first character following the [ is a !  or a  ^ then  any  character not enclosed is matched.

.[!.]* matches a string which starts with a period but the second character of the string is not a period.

---

### Post by CaptainMark on 2009-12-21
Thanks, good to know

---

