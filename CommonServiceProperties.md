# Setting Common Service Properties #

Daemoniq supports for setting up common service properties via the app.config file. Attributes like `serviceName`, `displayName`, `description` and `serviceStartMode` are supported by the `service` element.

The sample configuration file below illustrates hosting 2 instances of the same service (each one with a different serviceName) in one process.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="daemoniq" type="Daemoniq.Configuration.DaemoniqConfigurationSection, Daemoniq" />
    <section name="castle" type="Castle.Windsor.Configuration.AppDomain.CastleSectionHandler, Castle.Windsor" />
  </configSections>
  <castle>
    <components>
      <component id="Dummy"
                 service="Daemoniq.Framework.IServiceInstance, Daemoniq"
                 type="Daemoniq.Samples.DummyService, Daemoniq.Samples">
      </component>     
    </components>
  </castle>
  <daemoniq>
    <services>
      <service
        serviceName="Dummy"
        displayName="Dummy Service"
        description="This is a dummy service"
        serviceStartMode="Manual">
      </service>
    </services>
  </daemoniq>
</configuration>
```

_Note: acceptable values for `serviceStartMode` are `Automatic`, `Manual` and `Disabled`._