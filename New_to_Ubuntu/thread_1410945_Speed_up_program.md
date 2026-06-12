---
title: "Speed up program"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-19
I have a c program that I am trying to speed up and I ran across something that might help. There is a module that is called millions of times yet it executes less than 10% of those times it is called. 

The first thing that the program does upon entering said module is perform an if-then-else statement. But it passes the initial if statement only 10% of the time. I am not sure of the overhead in gcc of calling a module, but it seems to me there must be a better way.

The idea is to put said test statement(if-then-else) right before the statement where  the module is called and if it fails do not call the module; and if it passes then call the module. Of course, the if-then-else statement that is currently in the module in question will be removed. It just seems to me that some significant speed-up can be realized by doing this.

I did not write this code, initially.

Any thoughts on this appreciated.

newport_j

---

### Post by talonmies on 2010-02-19
By doing that, you are only removing the function call overhead, which is only slightly more than negligible. Consider the following:

```

#include <sys/time.h>
#include <stdlib.h>
#include <stdio.h>

const unsigned int large = 200000000;

double  systimer(void)
{

    struct timeval tp;
    double result=0.0;

    if ( gettimeofday(&tp, NULL) != -1 )
    {
        result = (double)(tp.tv_sec);
        result += ((double)(tp.tv_usec))*1.0e-6;
    }

    return result;
}


unsigned int func1(const unsigned int input)
{
    return (input > large) ?  (input >> 4) : 1;
}

unsigned int func2(const int input)
{
    return input >> 4;
}

int main(void)
{
    unsigned int jmy, out;

    double start1 = systimer();
    for(out=0, jmy=0; jmy < (20 * large); jmy++) {
        out += func1(jmy);
        out -= rand() % (RAND_MAX >> 8);
    }
    double stop1 = systimer();

    double start2 = systimer();
    for(out=0, jmy=0; jmy < (20 * large); jmy++) {
        out += (jmy > large) ? func2(jmy) : 1;
        out -= rand() % (RAND_MAX >> 8);
    }
    double stop2 = systimer();

    fprintf(stdout, "%f %f\n", stop1-start1, stop2-start2);

    return 0;
}
```

Compiled with default options using gcc 4.3, that gives less than 5% difference in overall execution time. If your execution times are measured in days, then that might be important. If they are less than that, it strikes me as a trivial optimization that is probably about the last thing you would do if you objective was to speed up the code.

---

