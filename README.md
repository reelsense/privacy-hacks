# privacy-hacks
:squirrel: Privacy for Mac users at work or on shared computers.

I occasionally need access to files or messages from my personal Google accounts at work. I got tired of constantly have to sign into Chrome Incognito tabs every time, and I didn't want my personal Chrome profile and account credentials written to disk on a computer that's not mine.

* Work computer is not mine.
* Don't want my personal Chrome profile and account credentials written to disk and accessible by another user.
* Tired of signing into Chrome Incognito tabs all the time.
* Tired of this shit.

Solution:

* Move Chrome profile to encrypted disk image.
* Symlink profile back to `~/Library/Application\ Support/Google/Chrome/Default`
* Create **_Automator Application_** to mount _img_ then _open Chrome_.

>**_Automator Application_** > _Run Shell Script:_
>```
>hdiutil attach /Users/$USER/Dropbox/*.sparsebundle && sleep 2 && open -a Google\ Chrome
>```

_hdiutil_ will try and mount the _sparsebundle_ disk image and prompt you for the decryption password. If successful mounted it will open _Chrome_ in 2 seconds.

### **:warning: Remember to UNCHECK _"Remember this password in my keychain"_** 
