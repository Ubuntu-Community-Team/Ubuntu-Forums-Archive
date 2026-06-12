---
title: "Importing MS Office custom.dic to OOo"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-02-15
I've tried [Russ Phillips' macro]("http://www.linuxtopia.org/online_books/office_guides/microsoft_office_to_openoffice_migration/openoffice_migration_Custom_dictionaries_0603MG-ImportingOtherMSOFiles.html") but it appears to have been defeated by the large number of terms I was importing (about 2900) and only did a partial job (quite a few terms a missing).

Questions:
1) Anyone else run into this problem
2) Any solutions

Thanks.

---

### Post by Kellemora on 2009-02-15
Hi Paul

You're on the right page there!

We had problems with our custom dictionary growing too large and Mickey$oft would truncate it back to 64k I believe it was.  We would lose words and not know why until we discovered this limitation.

And I'm pretty sure the macro is limited to 2000 entries.

The way around this is to SPLIT your existing custom dictionary into two or more dictionaries and then importing them with the macro.

Open Office allows you to use ALL dictionaries you have installed or created.  This has been a handy feature for us!  As you can select and de-select certain dictionaries as needed.  This is particularly helpful when working in various fields that have similar words but spelled differently for each field.  A good example of this is in Taxonomy or also when working in the Kings English.
When I first started using OOoWriter, I was adding words to the Standard dictionary by mistake, because that was the default setting.

I don't remember how you split your custom dictionary anymore, but if I recall it was fairly simple to do back when we did it and made separate dictionaries for separate purposes.

Good Luck!

TTUL
Gary

---

### Post by paulchinnz on 2009-02-16
Thanks Gary. I went crude and tried copying and pasting from my custom.dic file into custom1.dic for the first 1500 entries and custom2.dic for the rest of the 1400+ entries, and tried to get the macro to import from them to standard.dic (kept getting a message about standard.dic having 2000 entries). No luck.

Questions:
1) Is there a limit to how many entries standard.dic can cope with
2) Anyone know how to import >2000 word entries from MS Office's custom.dic to OOo's standard.dic?

---

### Post by paulchinnz on 2009-02-20
Well slightly messy solution but did this:
1) Divided original MS Office custom.dic into two .dic files of about 1500 entries each
2) Created two new OOo dictionaries ('A-K' and 'L-Z')
3) Imported each of the MSO .dic files into the OOo dictionaries respectively
4) Enable new OOo dictionaries

If anyone finds a cleaner solution let me know.

---

### Post by Kellemora on 2009-02-21
Hi Paul

That's exactly what we had to do!

Perhaps I didn't explain it clear enough in my post?

But that's what I meant when I said you can have several dictionaries in OOo and it can see and use them all, or you can check of certain ones to not use that particular one.  Like as if you had a custom dictionary for the Kings English, it would cause you to miss many misspelled words in common English.  Or when using Latin names too, etc.

I did a lot of them by hand also, by loading a taxonomy table that I knew all the words were correct and just began clicking add on all of them that had a red underline.  Didn't take as long as I thought it would either.
In fact, I think I lost more time trying to convert that file than I did doing it by hand.

What I WISH is they had a way of REMOVING some words from the Standard Dictionary that are not correct.  It could just be my machine too!

Words like couldn't, didn't, won't, etc. sometimes show a red line under them for no reason.  You select the word of the same spelling from the list and the line goes away.  Weird!

Glad you got it sorted out and can get back to production!

TTUL
Gary

---

### Post by paulchinnz on 2009-02-21
Thanks Gary. Had thought you meant splitting the MS dictionaries and importing them into the same OOo dictionary.

1) Was this not successful because there's a limit to how many entries OOo dictionaries can cope with?
2) How can I mass delete dictionary entries in OOo (in MS you just opened up custom.dic in notepad and had your way highlighting and deleting, in OOo I've only found you can only do one word at a time)?

---

### Post by Kellemora on 2009-02-22
Hi Paul

I hate to sound like a dumb **** here.
But I just started playing with Ubuntu in August of 2008 and had only used it less than a month before deciding to convert my entire office over to Ubuntu.

Needless to say, this brought taking time to learn things down to do it now and get it done.  I burned many long nights after hours trying to get things working properly.  I didn't keep a lot of careful notes at that time as I was in a real bind.

Since then, I've got to learn more and study some and had time to work through problems and make notes in case I hit them again.

But at the time we converted our dictionaries over, only two gave us a problem and we split those on the Doze and moved them to two on the Ubuntu machines for Open Office.

I was fortunate that I already had separate dictionary files for different purposes, but on the Doze had to remember to select the correct one ahead of time.

I don't think I've ever had to remove words from the custom dictionaries before.  I honestly don't know HOW to even bring up a word in the dictionary to change it, unless I purposely mistype it to get a list that might include it.  But I do know the Dictionary is NOT the same thing as the SpellChecker.  The thing called Custom Dictionary (or selected name) is not really a dictionary, but just a spellchecker, like Hunsacker, that adds the words spelling you said to add to it.  I've seen those files playing around in the Doze and they look complicated to me, hi hi..... 
And I'm still trying to find out just WHERE things are hidden here in Ubuntu.  I can do a file search for my self-created hydroculture.dic which I know is on the machine and I can select it in OOoWriter easily enough.  But I've never found WHERE it is stored.  I wanted to open it to see if it was hard or simple layout.  I did find a file that lists it as one of the dictionaries under the section marked spellcheckers.  But have not found where on my hard drive it is stored.  And FIND can't find it either.  So I think, it just shows US it's using the filename hydroculture.dic but probably stores it under a totally different secret code name.

I have other irons in the fire so things like toying with finding the dictionary is truly on a back burner for the time being.

I remember back in the early days of Doze when spellcheckers were first becoming popular, it was no problem to simply add a list of names to the user part of the dictionary listing as it was plain text.  You just couldn't mess with anything above the row of stars or it wouldn't work at all.

Someday I'm going to try and learn programming again too!  But with a zillion programming languages out there now, which one.  PhP has been suggested since it could relate closer to some of the things I work with.  But I don't know C++ or is it CC+ seems like the most common.

If I get a chance to play around with the dictionaries again some day soon, I'll send you a message of what I find out.  You never know, we might be able to do things never dreamed possible in the Doze, hi hi.....

TTUL
Gary

---

### Post by paulchinnz on 2009-02-22
Thanks Gary. You bring up some interesting points, especially where is standard.dic (and other OOo 'dictionaries'/spellcheckers). Look forward to hearing from you and anyone else about this.

---

### Post by Kellemora on 2009-02-23
Hi Paul

I did find something of interest!

[http://user.services.openoffice.org/en/forum/viewtopic.php?p=362#p362]("http://user.services.openoffice.org/en/forum/viewtopic.php?p=362#p362")

Go down to response number 4

this gives a graphical display with numbers of WHAT each of the files are for and what they do in OOo.

Turns out they do NOT end in .dic but in .aff the custom added ones with our added words that is.  I found en_hydr.aff but no en_hydro.dic on my computer, but in the extension listing, it appears as hydroculture.dic as it should.  I checked the file size and added 5 new words and the en_hydro.aff file changed size.  I also ran my mirror program and that too is the only file that was copied over to the server in the logfile.

So bingo, I think that's it!

TTUL
Gary

---

### Post by paulchinnz on 2009-02-25
Great find. I see that's for Windows. Where is it in Ubuntu anyway?

---

### Post by Mike Gleason on 2011-11-08
Here is a Perl script that can do this for you.

```
#!/usr/bin/perl -w
#
# convert_text_to_ooo_dic.pl
# by Mike Gleason, 2011-11-08.
#
# Instructions:
#
# Save this file where you can find it after starting up a Terminal.
# Run "perl convert_text_to_ooo_dic.pl infile.txt outfile.dic" from
# the command prompt, where infile.txt is the name of your dictionary
# in text format (one word per line).  After running the program,
# outfile.dic will contain the converted file for use with OpenOffice.
#
# For example, if you have created a user dictionary named "standard",
# quit OpenOffice then rename outfile.dic to standard.dic and replace
# the file in $HOME/.openoffice.org/3/user/wordbook. Restart OOo to 
# see that it is now using your revised "standard" custom user
# dictionary.
#
# Also note that this program can directly convert Microsoft Office
# custom user dictionary files (tested up to Office 2003), as those
# files (e.g., CUSTOM.DIC) are simply sorted text files with a header
# line (and the header line is ignored by this program).
#
if ((scalar(@ARGV) != 2) || ($ARGV[0] eq $ARGV[1])) {
    printf STDERR ("Usage: %s <infile.txt> <outfile.dic>\n", $0);
    exit(2);
}

open(IN, "< " . $ARGV[0]) or die "Could not open input file for reading: $!\n";
open(OUT, "> " . $ARGV[1]) or die "Could not open output file for writing: $!\n";

my ($nwords) = 0;
my @words = ();
my ($len) = 0;

while (defined(my $word = <IN>)) {
    $word =~ s/[\r\n]+//g;
    # Skip empty lines and comment lines (helpful for MS Office 2003 .dic files)
    if (($word !~ /^\s*$/) && ($word !~ /^[\#\;\@\$]/)) {
        push(@words, $word);
    }
}

# Sort the words alphabetically, case-insensitively.
my @words_sorted = sort { lc($a) cmp lc($b) } @words;

my ($prevword) = "#";
for my $word (@words_sorted) {
    $len = length($word);
    next if (($word eq $prevword) || ($len <= 0) || ($len >= 32768));
    if ($nwords++ == 0) {
        # Print file header before first word.
        print OUT "\006\000WBSWG6\xFF\000\000";
    }
    print OUT pack("S", $len), $word;
    $prevword = $word;
}

close(IN);
close(OUT);
printf("* %d words output to %s.\n", $nwords, $ARGV[1]);
exit(0);
#EOF
```

And, if you need to go the other way, .dic to .txt, you can use this script instead:

```
#!/usr/bin/perl -w
#
# convert_ooo_dic_to_text.pl
# by Mike Gleason, 2011-11-08.
#
if ((scalar(@ARGV) != 2) || ($ARGV[0] eq $ARGV[1])) {
    printf STDERR ("Usage: %s <infile.dic> <outfile.txt>\n", $0);
    exit(2);
}

open(IN, "< " . $ARGV[0]) or die "Could not open input file for reading: $!\n";
open(OUT, "> " . $ARGV[1]) or die "Could not open output file for writing: $!\n";

my ($nwords) = 0;
my @words = ();
my ($len) = 0;
my ($got) = 0;

if ((sysread(IN, $header, 11) != 11) || ($header ne "\006\000WBSWG6\xFF\000\000")) {
    die "Bad header in " . $ARGV[0] .". This does not appear to be an OpenOffice dictionary file.\n";
}

while (1) {
    if (($got = sysread(IN, $len, 2)) != 2) {
        die "Bad word format.\n" if ($got == 1);
        last;
    }
    $len = unpack("S", $len);
    if (($got = sysread(IN, $word, $len)) != $len) { die "Expecting a $len-character word, but only read $got characters.\n"; }
    $word =~ s/[\r\n]+//g;
    if (($word !~ /^\s*$/) && ($word !~ /^[\#\;\@\$]/)) {
        push(@words, $word);
        $nwords++;
    }
}

my @words_sorted = sort { lc($a) cmp lc($b) } @words;

my ($prevword) = "#";
for my $word (@words_sorted) {
    next if ($word eq $prevword);
    printf OUT ("%s\r\n", $word);
    $prevword = $word;
}

close(IN);
close(OUT);
printf("* %d words output to %s.\n", $nwords, $ARGV[1]);
exit(0);
#EOF
```

Cheers, Mike.

---

