This is Simple JSON Config, or sjcfg

It provides an easy interface to reading/writing JSON values from a file using
dot delimited fields.

Write commands:

```
sjcfg my.key value
sjcfg my '{"key": "value"}'
```

Result from either command, in sjcfg.json:
```
{
    "my": {
        "key": "value"
    }
}
```

Read commands:

```
sjcfg my.key
```
Result: `value`

```
sjcfg my
```
Result: `{'key': 'value'}`

Value can be plain text, or JSON. Plain text numbers are converted to numbers.

The file used is in order of precedence:

* The `-f` value as in `sjcfg -f file.json my.key` or `sjcfg -f file.json my.key value`
* The contents of the `$SJCFG_FILE` environment variable
* `$HOME/.config/sjcfg.json` , if `$SJCFG_FILE` is not defined.
* Program failure if `$HOME` is not defined.

