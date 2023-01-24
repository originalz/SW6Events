## Shopware 6 Events
### Common Shopware event directories
```bash
vendor/shopware/core/Checkout/ModuleName/ModuleNameEvents.php
```
```bash
vendor/shopware/core/Content/ModuleName/ModuleNameEvents.php
```
### EventSubscription
```php
<?php declare(strict_types=1);

namespace Conne\PluginName\Subscriber;

use Symfony\Component\EventDispatcher\EventSubscriberInterface;
use Shopware\Core\Framework\DataAbstractionLayer\Event\EntityWrittenEvent;
use Shopware\Core\Framework\DataAbstractionLayer\Event\EntityLoadedEvent;
use Conne\PluginName\Service\ServiceName;

class SubscriberName implements EventSubscriberInterface
{
    // Don't forget the dependency injection in the services.xml
    private ServiceName $serviceName;

    public function __construct(ServiceName $serviceName)
    {
        $this->serviceName = $serviceName;
    }

    public static function getSubscribedEvents(): array  
    {
        return [  
            ProductEvents::PRODUCT_TRANSLATION_WRITTEN_EVENT => 'onProductTranslationWritten',
            ProductEvents::PRODUCT_TRANSLATION_LOADED_EVENT  => 'onProductTranslationLoaded',
        ];  
    }

    public function onProductTranslationWritten(EntityWrittenEvent $event): void
    {
        // Call injected custom service on event written
        $this->serviceName->method($param);
    }

    public function onProductTranslationLoaded(EntityLoadedEvent $event): void
    {
        // Call injected custom service on event loaded
        $this->serviceName->method($param);
    }
}
```
