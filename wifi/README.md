In order to have a data store running locally (assuming that mirage tool stack is installed):

1. put server certificates under tls/
2. pin and install a package: ucn-eu/pih-store
```
opam pin add pih-store https://github.com/ucn-eu/pih-store.git
```
3. then from a terminal, type
```
mirage configure
mirage build
./mir-wifi
```
a unikernel should run locally with tls ports 4433, you can change them in the file server_config.ml

right now, the store take no assumption about the orgnisation of data in the store, when you try to read, just make sure you have already written something in the same path


* `GET /path/to/your/data`      should return your data under the path
* `GET /path/of/directory/all`  concatenate all the data under the directory(not recursive), return them as a json array, make sure they are right formatted json data, otherwise...
* `GET /path/of/directory/list`  list all the data files under the directory 
* `POST /path/to/your/data`     create or update the data