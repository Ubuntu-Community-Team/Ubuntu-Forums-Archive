---
title: "Help handling unrecognized token in Lex"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by dissectcode on 2011-05-04
I am working with a Lex file that was created as a stand-alone parser for a Linux application at work. The file has a lot of "rules" (like the example I gave below for parsing a filename) which parses the command line input. It does not handle unrecognized input, which is what I am having trouble with.

```

%%
-F {
    BEGIN FILENAME;
}
<FILENAME>[ ]+
<FILENAME>[\.]{0,2}[/_a-zA-Z0-9\.\-]+ {
    if ( filename ) 
    {
        free( filename );
        filename = NULL;
    }
    filename = strdup( yytext );
}


.    { printf("Invalid input: %s\n",yytext); exit(1); }    // what i am trying to do, doesn't work
%%

main(void)
{
......

```I found an online suggestion of putting that "Invalid input" message to catch tokens that were not parsed, but the lex file says Invalid input: after every command. Does anyone know what I should be doing?

I want it to exit with an error message when I type junk:

```

>mytool -dlfdsjkfl

>mytool -f out.txt sdfdsfs

```here is current example output which prints the helper, but with the error message showing that the error is printed with valid commands too:

```

> mytool -h
Invalid input:

Helper
=====
Usage: mytool <options> <commands>
Copyright today.

```

---

