Every language has good and bad parts. Javascript has the most impressive features ever put into any computer language.
It also happens to have the most bad features of any language. 

NB: JSLint, ESLint were introduced to mitigate the use of the bad parts of the language.

There is no imperical evidence to support the benefits of one programming style over another.
Eg. 
```
myFunction() {
    //
}
```
OR 
```
myFunction() 
{
    //
}
```
A good answer may be to stay consistent. But in Javascript it should always be on the right. Here is why...

NB: Ken thompson was the creator of the language B, which inspired the creation of the language C which ends up inspiring many languages after.

### Example - Javascript allows returns of objects in functions, usually called constructors

## Works As Expected
```
return {
    ok: true
};
```

## Fails Silently (No error at compile or runtime)
```
return 
{ //UNREACHABLE CODE
    ok: false
};
```

### WHY DOES THIS FAILS?
Javascript was designed as a language for beginners, but it looks like the prohramming language C and C was not designed for beginners.
The decision could have been taken to design a new syntax but that was not taken. Instead a feature called Automatic Semi-Colon Insertion was
included to help fix missing semi colon insertions which were missed if beginners did not know where to place them for example. 
Due to this feature the above syntax would fail because a semi colon will be places after the return to correct the syntax.

NB: All this is UNREACHABLE CODE because of the return

This would leave a hanging block which is an accepted syntax in javascript.
javascript syntax allows statements to have labels for example:
This means the ok: statement passes as a label.

The false statement qualifies as a useless expression statement. Would have been better if the language only supported assigment (=) and statement invokation () 
in these scenarios. Everything else should have triggered syntax errors.
However for the useless expression statement to work we need to end the false literal with a semi colon, which javascript does for us automatically.
Finally blocks do not have semi colons but this is also not a problem because javascript has the empty statement feature which allows you to use
as many semi colons as you like. All of them would be cleared up. 


```
outerloop: // This is the label name
for(...) {
    continue outerloop;
}
```

```
return;
{
    ok: false; <= js inserted semi colon // label
};
```

NB: You will never experience this if you always place your curly braces on the right.
NB: As a programmer you should prefer styles or forms that are error resistant. 


