# git crypt + keybase test

## Initial setup

Follow/Track the people on keybase you want to allow access to your secrets
Import keys (you already track the other people)

    keybase pgp pull [<usernames...>]

List keys

    gpg --list-keys

Trust the keys you want to allow access

    gpg --edit <email@address.com>
    gpg> trust

    Please decide how far you trust this user to correctly verify other users' keys
    (by looking at passports, checking fingerprints from different sources, etc.)

      1 = I don't know or won't say
      2 = I do NOT trust
      3 = I trust marginally
      4 = I trust fully
      5 = I trust ultimately
      m = back to the main menu

    Your decision? 5
    Do you really want to set this key to ultimate trust? (y/N) y

Init git-crypt

    git-crypt init

`add-gpg-user` them

    git-crypt add-gpg-user <email@address.com>

Add a [`.gitattributes`](.gitattributes) file which lists the files to encrypt

    mysecretfile.txt filter=git-crypt diff=git-crypt

## After cloning

    git-crypt unlock
