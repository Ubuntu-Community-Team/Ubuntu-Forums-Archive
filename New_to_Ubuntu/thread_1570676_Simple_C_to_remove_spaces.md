---
title: "Simple C to remove spaces"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by navaneethan on 2010-09-08
I have done this program to remove the space punctuation etc only alphanumeric has been considered but it stucks to get output
what is the problem actually?why it doesn't print exactly plz give suggestion

#include<stdio.h>
#include<conio.h>
#include<ctype.h>
void main()
{
	char s[30],p[30];
	int i=0,j=0;
	clrscr();
	printf("Enter the String");
	scanf("%s",s);
	while(s[i]!='\0')
	{
		if(isalpha(s[i]))
		{
			p[j]=s[i];
			j++;
			}
			i++;

	}
	printf("The alpha string is %s",p);
	getch();
}

---

### Post by JKyleOKC on 2010-09-08
I think you need to set all 30 bytes of both buffers to 0 before getting input. You're looking for the zero-byte end-of-string flag, but C normally allocates local variables on the stack and it's quite possible that there's no zeroed byte anywhere near. Another solution would be to check for i and j going past 30, and breaking the loop if that happens.

If this is homework, I hope your instructor has emphasized the need for "sanity checking" at every point within a program. Machines do only what you tell them to do, but they are totally literal about it and have no common sense to apply!

---

### Post by col48 on 2010-09-08
You should do both the things JKyleOKC suggests.  You are at the mercy of the person running the program in that if it is possible to give you some input which will break the program, sooner or later someone will.

To help debug, I'd print i,j and s[i] each time into the loop.

As it stands, if there is no zeroed byte you will be importing into your program whatever is thrown at it - could be hundreds or thousands of characters if none of them is zero - and there is the possibility of overwriting memory which contains code which will be executed later; if the user is malicious this could be virus code.  You do need to be careful!.

---

### Post by gzarkadas on 2010-09-08
I believe, because the program is simple, that the reason it does not print is that you do not finish the input to it from the command line; you must end your input with ^D (Ctrl+D), probably twice.

Now, apart from what the previous poster have mentioned, which is all correct, you definitely must correct a severe vulnerability in your program: The " scanf("%s",s); " is inherently insecure, because you have no way to enforce the user to input less than 30 characters. You should use **getchar** instead inside a loop.

See my example below (have removed conio.h stuff to test; you can put it back if you like).

```

#include<stdio.h>
#include<ctype.h>
int main()
{   
    printf("Enter the String:");
    char p[30];
    int i = 0;
    char c = (char) getchar();
    while (c && c != EOF && i < 29)
    {   
        if (isalpha(c))
            p[i++] = c;
        c = (char) getchar();
    }
    p[i] = (char) 0;   /* end the string */
    printf("\nThe alpha string is %s\n", p);
    return 0;
}

```

---

### Post by navaneethan on 2010-09-10
Is it if we use scanf means we have to fill full memory which we allocated for the particulare variable?gets() no needed ?

---

### Post by gzarkadas on 2010-09-10
scanf() as you coded it, will try to put all input produced by the user to your string buffer ('all' is here the keyword). However, your string buffer will always have a limited, fixed length. It doesn't matter if it is 30 or 300 or 30000; it is limited, while your C library input routine allows the user to supply a practically unlimited amount of  input. This code is therefore open to buffer overflow and all of its dangerous consequences (the most dangerous: arbitrary code execution).

gets() has the same flaw because it also does not let you specify the maximum number of bytes that you want returned. If the user supplies a very long line, it may overflow your buffer.

If you want to read input directly to a string use fgets(), with stdin as the 'stream' argument. It allows you to specify the maximum input size; set it to that of your buffer. You need to supply code to handle the case where an input line exceeds the size of your buffer; make it form a loop because it may exceed the size more than one time (n > 2).

To terminate a string it is enough to append at the end just a single zero; there is no need to assign to the part of your buffer that follows the first null character.

---

