# PHP-CSRF

## Usage
```<?php ```
```session_start(); ```
```include 'csrf.class.php'; ```

```$csrf = new csrf(); ```


```// Generate Token Id and Valid```
```$token_id = $csrf->get_token_id();```
```$token_value = $csrf->get_token($token_id);```

```// Generate Random Form Names```
```$form_names = $csrf->form_names(array('user', 'password'), false); ```


```if(isset($_POST[$form_names['user']], $_POST[$form_names['password']])) {```
```        // Check if token id and token value are valid.```
```        if($csrf->check_valid('post')) {```
```                // Get the Form Variables.```
```                $user = $_POST[$form_names['user']];```
```                $password = $_POST[$form_names['password']];```

```                // Form Function Goes Here```
```        }```
```        // Regenerate a new random value for the form.```
```        $form_names = $csrf->form_names(array('user', 'password'), true);```
``` } ```

``` ?>```

``` <form action="index.php" method="post">```
``` <input type="hidden" name="<?= $token_id; ?>" value="<?= $token_value; ?>" />```
``` <input type="text" name="<?= $form_names['user']; ?>" /><br/>```
``` <input type="text" name="<?= $form_names['password']; ?>" />```
``` <input type="submit" value="Login"/>```
``` </form>```
